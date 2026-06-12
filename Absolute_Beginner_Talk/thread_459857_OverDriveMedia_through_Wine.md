---
title: "OverDriveMedia through Wine?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Yules on 2007-05-31
Hello,
I'm very new to Ubuntu, and only vaguely understand how everything works. I tried installing OverDrive Media Console for library audio books using Wine and could not figure it out.  The installation dialog box never appeared, Instead, a new file was created to the desktop called VSDCA_VsdLaunchConditions.Log.
And this was in the terminal:

baberoni@Baberoni-Workstation:~$ cd Desktop
baberoni@Baberoni-Workstation:~/Desktop$ wine ODMediaConsoleSetup.exe
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ec08
fixme:wintrust:WTHelperProvDataFromStateData (nil)
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ec08
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ec08
fixme:wintrust:WTHelperProvDataFromStateData (nil)
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ec08
fixme:wintrust:WinVerifyTrust 0x10024 {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ec0c
fixme:advapi:LookupAccountNameW (null) L"baberoni" (nil) 0x33e7b0 (nil) 0x33e7ac 0x33e7b8 - stub
fixme:advapi:LookupAccountNameW (null) L"baberoni" 0x182378 0x33e7b0 0x172ac8 0x33e7ac 0x33e7b8 - stub
fixme:msi:MsiGetMode 1 4
err:msi:ITERATE_Actions Execution halted, action L"VSDCA_VsdLaunchConditions" returned 1603


Does that mean OverDrive will not work in Ubuntu? Is there anything else I could try?
Thanks,
Yules

---

### Post by southernman on 2007-05-31
What is the output of the log file on your desktop?

---

### Post by Yules on 2007-05-31
Output log file:
TASK	CoInitializeEx - COM initialization Apartment Threaded

TASK	Enumerating table using SQL statement: SELECT * FROM `_VsdLaunchCondition`

TASK	MsiGetActiveDatabase

TASK	MsiDatabaseOpenViewW - Prepare Database to view table

TASK	MsiViewExecute - Open Database view on table

Checking a launch condition

TASK	Getting the condition to evaluate

TASK	MsiRecordGetStringW - Fetching value

TASK	MsiRecordGetStringW - Getting value from column 1

TASK	Evaluating condition 'WMP9_EXISTS <> ""'

RESULT	Condition is false

TASK	MsiRecordGetStringW - Fetching value

TASK	MsiRecordGetStringW - Getting value from column 2

TASK	MsiSetPropertyW - Setting Property Value

TASK	MsiSetPropertyW - Setting property HideFatalErrorForm to TRUE

RESULT	Custom Action Succeeded.	uiRet = 1603


thanks

---

### Post by southernman on 2007-05-31
Thanks for posting the output Yules, Unfortunately, it doesn't tell me anything I can help you with.

I did look at winehq and don't find overdrive listed in the apps database.

I guess it will not work in wine, therefore no Ubuntu either. Someone else may be able to disprove that statement... or confirm it.

---

### Post by Yules on 2007-05-31
Steve,
Thank you very much.
yules

---

### Post by southernman on 2007-05-31
> **Yules said:**
> Steve,
Thank you very much.
yules
Your very welcome, Yules.

I did see something (MediaCenter I think it was) in the database although, I think it was more for movies and music... don't think it said anything about library audio books.

I am certain that something is available, either "for" linux os's or that "can" run under wine... to suit your fancy.

---

