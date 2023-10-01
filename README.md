
# Performance Testing with JMeter - README

## Table of Contents
1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
3. [Usage](#usage)
    - [Creating a Test Plan](#creating-a-test-plan)
    - [Configuring Test Elements](#configuring-test-elements)
    - [Running Tests](#running-tests)
    - [Analyzing Results](#analyzing-results)
4. [Best Practices](#best-practices)
5. [Troubleshooting](#troubleshooting)
6. [Contributing](#contributing)
7. [License](#license)

---

## Introduction

This README provides a comprehensive guide to performing performance testing using Apache JMeter. Performance testing is essential for evaluating the speed, scalability, and stability of your application under various load conditions.

**Apache JMeter** is an open-source tool designed for load testing, stress testing, and performance testing of web applications, databases, and other services. This guide will help you get started with JMeter and walk you through the process of creating and running performance tests.

## Getting Started

### Prerequisites

Before you begin, ensure that you have the following prerequisites in place:

1. **Java**: JMeter is a Java-based application, so you need to have Java (JRE or JDK) installed on your system. You can download Java from [Oracle's website](https://www.oracle.com/java/technologies/javase-downloads.html) or use an open-source alternative like OpenJDK.

2. **Apache JMeter**: Download the latest version of Apache JMeter from the official website: [Apache JMeter Downloads](https://jmeter.apache.org/download_jmeter.cgi).

### Installation

1. **Install Java**: Follow the installation instructions for your specific operating system to install Java.

2. **Install JMeter**:

   - Extract the downloaded JMeter archive to a directory of your choice.
   - Navigate to the JMeter bin directory (`<JMETER_HOME>/bin`).

## Usage

### Creating a Test Plan

1. Launch JMeter by executing the `jmeter.bat` (Windows) or `jmeter.sh` (Linux/macOS) script located in the `bin` directory.

2. Create a new test plan by right-clicking on the "Test Plan" node in the left-hand tree view and selecting "Add > Threads (Users) > Thread Group."

3. Configure your Thread Group to define the number of users, ramp-up time, and loop count.

4. Add samplers (HTTP Request, JDBC Request, etc.) to your test plan to simulate user actions.

### Configuring Test Elements

- **Listeners**: Listeners help you collect and view test results. Add listeners such as "View Results Tree," "Summary Report," or "Aggregate Report" to your test plan.

- **Timers**: Timers can be used to simulate think times between user requests. Common timers include "Constant Timer" and "Gaussian Random Timer."

- **Assertions**: Assertions allow you to set conditions that must be met for a request to be considered successful. Use assertions like "Response Assertion" and "Duration Assertion."

### Running Tests

1. Save your test plan.

2. Click the "Run" menu, then select "Start" to begin your test.

3. Monitor test progress using the listeners you added.

[**Test Plan**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#test-plan)

Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the jMeter version you are using)

- Name: Users
- Number of Threads (users): 1 to 13
- Ramp-Up Period (in seconds): 10
- Loop Count: 1
  - The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.
  - All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.
  - Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.
  - The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.

[**Collection of API**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#collection-of-api)

- Run BlazeMeter
- Collect Frequently used API
- Save JMX file then paste => **apache-jmeter-5.6.2\bin**

[**List of API**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#list-of-api)

- <https://www.opencart.com/index.php?route=support/contact>
- <https://www.opencart.com/index.php?route=account/login>
- <https://www.opencart.com/index.php?route=account/register>
- <https://www.opencart.com/index.php?route=cms/feature>
- <https://www.opencart.com/index.php?route=marketplace/extension>

**OR**

[**Load the JMeter Script**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#load-the-jmeter-script)

- File > Open (CTRL + O)
- Locate the "Git-project.jmx" file contained on this repo
- Continue open Git-project\_t1 to Git-project\_t14
- Open those file
- The Test Plan will be loaded

![p1](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture1.png)

[**Test execution (from the Terminal)**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#test-execution-from-the-terminal)

- JMeter should be initialized in non-GUI mode.
- Make a report folder in the **bin** folder.
- Run Command in **jmeter\bin** folder.

[**Make csv file**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#make-csv-file)

- **n**: non GUI mode
- **t**: test plan to execute
- **l**: output file with results
```bash
jmeter -n -t Git-project_t13.jmx -l report/Git-project_t13.csv
```
![p3](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture3.png)

[**Make jtl file**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#make-jtl-file)
```bash
jmeter -n -t Git-project_Endurence_14s.jmx -l report\Git-project_Endurence_14s.jtl
```

Then continue to upgrade Threads(1 to 14) by keeping Ramp-up Same.

![p5](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture5.png)

[**JTL file**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#make-html-file)

![p6](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture6.png)


After completing this command

[**Make html file**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#make-html-file)
```bash
jmeter -g report\Git-project_Endurence_14s.jtl -o report\Git-project_Endurence_14s.html
```
- **g**: jtl results file
- **o**: path to output folder
  
![p8](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture8.png)

![p9](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture9.png)

[**HTML Report**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#html-report)

**Number of Threads 1 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 2 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 3 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 4 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 5 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 6 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 7 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 8 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 9 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 10 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

[**Load testing Report**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#load-testing-report)

![p12](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture12.png)

[**Summary**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#summary)

- While executed 14 concurrent request, found 140 request got connection timeout and error rate is 48.57%.
- Server can handle almost concurrent 65 API call with almost zero (0) error rate.

[**Stress Testing**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#stress-testing)

Stress Testing is a type of software testing that evaluates how the software responds under extreme conditions. It verifies how robust a system will be, and its response capabilities and error handling when it is subjected to conditions where its normal functioning can be compromised.

**Number of Threads 11 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 12 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

**Number of Threads 13 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

[**Spike Testing**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#spike-testing)

Spike testing is a type of performance testing where the demand for an application is suddenly and drastically increased or decreased. Spike testing's objective is to ascertain how a software program will behave under highly variable traffic conditions.

**Number of Threads 14 ; Ramp-Up Period 10s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p13](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture13.png)|![p14](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture14.png)|

[**Endurance Testing**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#endurance-testing)

An application may be put through endurance testing to see if it can handle the processing load that will be placed on it over an extended period of time. Memory usage is tracked throughout endurance tests to identify potential issues.

**Start Threads count 13s ; Initial Delay 0s ; Start up Time 10s ; Hold load for 14s ; Shutdown Time 0s**

|**Requests Summary**|**Errors**|
| :-: | :-: |
|![p10](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture10.png)|![p11](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture11.png)|

![p15](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture15.png)

[**Read Test Data from CSV file in Jmeter**](https://github.com/musthafiz/Performance-testing-for-OpenCart-Website/blob/main/README.md#read-test-data-from-csv-file-in-jmeter)


- Create a CSV file in the test suite folder and add test data to it.

![p16](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture16.png)

- Add a Config Element CSV Data Set Config in Jmeter.
  
![p17](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture17.png)
- Configure ' CSV Data Set Config ' based on the need such as providing path of CSV file and variable names and other configs.
  
![p18](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture18.png)
- Run the test to see if data from the CSV file is read and populated in the results.
- Run the test to see if data from CSV file is read and populated in the results.

**Number of Threads 13 ; Ramp-Up Period 5s**
![p19](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture19.png)

![p20](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture20.png)

![p21](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture21.png)

![p22](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture22.png)

![p23](https://github.com/tofayel143/Performance_Testing/blob/master/Image/Picture23.png)

### Analyzing Results

After the test has completed:

- Review the results in the various listeners to identify performance bottlenecks and issues.

- Generate reports using tools like JMeter Plugins or export results in various formats for further analysis.

## Best Practices

- **Parameterization**: Use CSV Data Set Config or User Defined Variables for parameterization of requests.

- **Think Time**: Realistic think times between requests are crucial for accurate testing.

- **Correlation**: Use Regular Expressions Extractor or JSON Extractor to correlate dynamic values in responses.

- **Distributed Testing**: For large-scale testing, consider setting up distributed JMeter testing across multiple machines.

- **Resource Cleanup**: Ensure your tests include proper cleanup steps to avoid resource leaks.

## Troubleshooting

- Check the JMeter logs (`jmeter.log`) for error messages and stack traces.

- Consult the [JMeter Documentation](https://jmeter.apache.org/usermanual/index.html) for detailed information on JMeter components and features.

## Contributing

Contributions to this README or JMeter itself are welcome. If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details. Apache JMeter is also licensed under the Apache License 2.0.
