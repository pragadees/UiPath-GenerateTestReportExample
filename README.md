# UiPath-GenerateTestReportExample
Sample project explaining the usage of GenerateTestReport library.

Follow below steps to use the GenerateTestReport library component.
1. Download and install the [GenerateTestReport](https://github.com/pragadees/UiPath-GenerateTestReport) library component in your project from Git.
2. Surround the test case with Try Catch block and define your test case under Try block. Use Info level logs to add more information to the test case logs.
3. Have an Assert activity in the catch block to set the status of the test case to Failed in case of any exceptions.
4. Under Finally call the 'Generate Test Report' library component and pass the below required parameters.
	### Input arguments
	- ContinueOnException (Recommended to set this value to True. Otherwise, the test case status will be set to 'Failed', if any exeception is raised by the 'Generate Test Report' component
	- OrchestratorFolderPath (Mandatory. UiPath Orchestrator folder path where the test set is defined and executed. Recommended to have this as asset.)
	- Output folder (Optional folder location where the generated report needs to be saved. The test report will be saved in the library nuget folder if this argument is left empty. Make sure the folder path is reachable from the testing robot.)
	- ReportType (Mandatory. Valid values are 'html', 'excel'. Recommended to use HTML report which contains more information such as execution logs.)
	
	### Output arguments
	- GeneratedReportPath (Full file path to the generated output report. Use this in subsequent activities such as exchange activity to notify user)
	- The below output arguments are self descriptive and can be used to include the test set execution stats in email body while notifying the users
		- OverallStatus
		- TestCasesCancelled
		- TestCasesFailed
		- TestCasesPassed
		- TestSetName
		- TotalTestCases

5. Refer **TestReportGen Execution Results.html** for sample html report generated using this project.

**Please note this component will only work when a test set is executed from Orchestrator and not while running/debugging test cases using Studio.**
