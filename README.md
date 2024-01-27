Project 5 - HTML Emails

Create Curl Log Entry

Allow User Abort [ Off ]: Prevents users from interrupting the script once it starts.

#Validate context: This is a comment for clarity, not an executable line.

If [ not ContextIsBasedOn ( Email::ID ) ]: Checks if the current context is based on a specific Email::ID.

Exit Script [ Result: JSONSetElement... ]: Exits the script, returning a JSON object with error details if the context is invalid.

End If: Closes the 'If' statement.

If [ Get ( WindowMode ) ≠ 0 or Get ( FoundCount ) = 0 ]: Checks if the window mode is not normal or if no records are found.

Exit Script [ Result: JSONSetElement... ]: Exits the script, returning a JSON object with error details if the previous condition is true.

End If: Closes the 'If' statement.

#Unpack the script parameter: Comment indicating the start of script parameter processing.

Set Variable [ $param; Value:Get ( ScriptParameter ) ]: Stores the script parameter in a variable.

11-28. Set Variable [ $variableName; Value:... ]: Assigns various parameters (like timestamp, error code, error message, etc.) to different variables.

#Create the cURL log record: Comment indicating the start of the log record creation.

30-42. Set Field [ fieldName; value ]: Sets the values of different fields in the cURL log record.

#Return result: Comment indicating the end of the script.

Exit Script [ Result: JSONSetElement... ]: Exits the script, returning a JSON object indicating successful completion.

Duplicate Email

Allow User Abort [ Off ]: Disables the ability for the user to cancel the script once it has started.

#Validate context: A comment for clarity, indicating the start of context validation.

If [ not ContextIsBasedOn ( Email::ID ) ]: Checks if the current context is based on a specific Email::ID.

Exit Script [ Result: JSONSetElement... ]: If the context is not based on Email::ID, the script exits, returning a JSON object with an error code and message.

End If: Ends the 'If' block.

If [ Get ( WindowMode ) ≠ 0 or Get ( FoundCount ) = 0 ]: Checks if the window mode is not normal or no records are found.

Exit Script [ Result: JSONSetElement... ]: If the condition is true, exits the script with an error.

End If: Ends the 'If' block.

#Duplicate email and related child attachment records: A comment indicating the start of the email duplication process.

Freeze Window: Prevents screen refresh to speed up script execution.

11-22: Variables are set for the original email and attachment IDs, and the email record is duplicated.

23-46: The script duplicates related attachment records and associates them with the new email record.

Exit Script [ Result: JSONSetElement... ]: The script exits, returning a success code.

Get Curl Command

Allow User Abort [Off]: Disables interruption of the script by users.

#Figure out where the message mail file and trace file will go: A comment indicating the start of file path setup.

Set Variable [$folderPath, $emailMessageFileName, $emailMessageFilePath, $traceFileName, $traceFilePath]: Defines file paths and names for email message and trace files.

#Export the message mail file to the desktop: Comment indicating the export section.

If [not IsEmpty (cURLLog::Message)]: Checks if the message field is not empty.

Create/Open/Write to/Close Data File: These commands handle the creation and writing to the email message file.

#Copy the cURL command to the user's clipboard: Comment for the cURL command copy section.

Set Variable [$curlCommand]: Forms the cURL command.

Set Field [cURLLog::cURLOptions; $curlCommand] and Copy [cURLLog::cURLOptions]: Updates and copies the cURL command to clipboard.

Revert Record/Request [No dialog]: Reverts any unsaved changes to the current record.

#Show message to the user: Comment indicating the start of user messaging section.

Set Variable [$$MESSAGE]: Defines the message to show to the user.

New Window: Opens a new window to display the message.

Go to Object [Object Name: "Button: OK"]: Focuses on the OK button.

Exit Script [Result: 0]: Exits the script.

Send Email using insert from URL

Allow User Abort [Off] and Set Variable [$isClientDapi...]: Sets initial conditions and variables based on the application version and system platform.

If [conditions]: Checks if the client is Data API or WebDirect and if so, performs the script on the server.

Insert Calculated Result [$timer...]: Sets a timer for performance tracking.

Check FileMaker version: Ensures the FileMaker version is 18 or higher.

Unpack the script parameter: Extracts parameters like SMTP settings and email details from a JSON parameter.

Set Variables [$sendTimestamp...]: Sets variables for timestamp and SMTP URL.

Build cURL options and message: Creates the cURL options and the email message, including handling recipients and attachments.

Insert from URL: Executes the cURL command to send the email.

Error Handling and Result Building: Manages error capture, constructs the result in JSON format including error codes, messages, and debug information if required.

Exit Script: Returns the result and exits the script.

Send Email

User Abort Control and Timer Initialization: Disables user interruption and initializes a timer for performance tracking.

Context Validation: Ensures the script runs in the correct context related to Email::ID.

SMTP Password Prompt: If necessary, prompts the user for the SMTP password.

SMTP and Email Parameter Preparation: Sets up parameters for SMTP configuration and email details like sender, recipients, subject, and body.

Attachment Handling: Processes email attachments, encoding them in base64.

Execute Email Sending: Calls a subscript to send the email using the prepared parameters.

Result Unpacking: Extracts results from the subscript execution, including error handling.

cURL Log Entry Creation: Generates a log entry for the cURL operation.

User Notification and Script Exit: Informs the user about the operation result and exits the script.

Project 4 -  Exchange currency

Backup

Disallow User Interruption & Assign Variables: Sets up essential variables based on the system platform and current timestamp.

Context Precautions: Includes checks for user's platform and multi-user status, showing relevant messages and exiting if conditions are not met.

Create Folders: Depending on the platform (Windows, Mac, or other), it executes different procedures to create necessary backup folders.

Pause for Folder Creation: Briefly pauses to ensure folder creation is complete.

Make a Compressed Backup: Saves a compacted copy of the current FileMaker file to the defined backup location.

This script ensures a systematic backup process, adapting to different platforms and handling folder creation efficiently.

Get rates

Disallow User Interruption and Enter Browse Mode: Sets the script to run without interruption and enters a specific mode for viewing and interacting with records.

Set Variables for Currency and Date Range: Assigns values to variables like base currency, currency codes, and date range for exchange rates.

Define Scope and URL Parameters: Determines whether to fetch latest rates or historical data based on the date range and constructs URL parameters accordingly.

Construct API Request URL: Combines the base API URL with the criteria derived from previous steps to form the full request URL.

Execute API Call: Uses "Insert from URL" to call the API and store the JSON response.

Format and Sort JSON Response: If specified, formats and sorts the JSON data for better readability and sets it in a field.

Commit Changes: Finalizes the records/requests.

Project 3,2,1 - Pledges , car and basics

Talk About the Custom layout use and everything

In FileMaker, the "Sort Records" step is used to organize records in a specific order based on one or more fields. You can specify ascending or descending order for each field. This is useful for viewing records in an organized manner, such as alphabetically or by date.

The "Go to Field" script step, on the other hand, is used to navigate directly to a specific field in the layout. This is particularly helpful in guiding the user's focus to a particular part of a record for viewing or editing, such as moving to a specific entry field immediately after a new record is created.
