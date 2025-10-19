# SKU Test Tool GUI

The **SKU Test Tool GUI** is a Python and Tkinter-based automation tool designed to download, extract, and execute SKU test cases. Upon completion, it automatically compresses the results and sends email notifications to designated recipients. The tool supports FTP file management, ChromeDriver updates, TempLog monitoring, and automated batch test execution.

## Features

* **FTP File Management**

  * Connect to an FTP server to download SKU test files from a specified directory
  * Automatically extract `.7z` files and clean up old versions

* **Batch Test Execution**

  * Support selection of multiple SKU batch test files
  * Automatically run batch files and monitor `TempLog/matrix.xlsx` generation

* **ChromeDriver Management**

  * Automatically download the latest ChromeDriver
  * Replace the ChromeDriver used by the test tool and clean temporary files

* **Email Notifications**

  * Send test result reports via Gmail SMTP
  * Manage recipient lists and save historical recipients

* **GUI Operation**

  * Add, delete, and select historical recipients
  * Real-time log display to track test progress
  * START / STOP / CLEAN buttons to control the testing process

* **Network Management**

  * Automatically detect local network gateway
  * Set IP metric to prioritize DUT or external network connections

---

## Requirements

Ensure the following environment and packages are installed:

* Python 3.9 or higher
* Required pip packages:

  ```bash
  pip install requests py7zr psutil
  ```
* Windows OS (the program relies on `netsh` commands to set IP metrics)
* Gmail account with an App Password (used to send emails)

---

## Usage

1. **Launch the GUI**

   ```bash
   python main.py
   ```

   The main window will display the recipient list, test case selection box, and log area.

2. **Manage Recipients**

   * Enter a Gmail address and click **Add Recipient**
   * Click **Select Historical Email** to use previously saved recipients
   * Click **Delete** to remove unwanted recipients

3. **Select Test Cases**

   * Choose the SKU test case to run from the left panel (single selection)

4. **Start / Stop Testing**

   * Click **START** to begin downloading, extracting, and executing tests
   * Click **STOP** to immediately stop all background threads
   * The log area displays progress and any errors

5. **Generate Reports and Send Emails**

   * Upon test completion, `TempLog` is automatically compressed to generate a report
   * Emails are automatically sent to all recipients

6. **Clear Logs**

   * Click **CLEAN** to clear the log display

## Project Structure

```
SKU-Test-Tool/
├─ main.py                   # Main program
├─ chromedriver/             # ChromeDriver download and replacement folder
├─ email_log.json            # Historical recipient records
└─ README.md                 # Project documentation
```

## Notes

* Ensure the FTP account and password are correct and the target directory exists
* Gmail email sending requires an App Password
* Make sure you have permission to execute batch files and modify network settings
* Do not manually delete `TempLog` or test directories during testing
