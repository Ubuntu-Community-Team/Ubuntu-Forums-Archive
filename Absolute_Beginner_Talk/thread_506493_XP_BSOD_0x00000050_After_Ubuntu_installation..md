---
title: "XP BSOD 0x00000050 After Ubuntu installation."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Wiebelhaus on 2007-07-21
(This is not a support thread , nor a "Ubuntu DID THIS!" , I'm simply dropping this into the search pool just in case someone runs into it , I have no idea how to explain this but it can't be a coincidence that after a Ubuntu installation with file transfer that this happened , an anomaly if you will)

After a Ubuntu installation on two SATA drives using the file & settings transfer function , XP on first - Ubuntu on second you receive a BSOD From XP,  either  0x00000050 or 0x0000008E pointing at the nv4_mini.sys , the first is a direct Stop error , the second not so much.

This is the[ fix:]("http://support.microsoft.com/kb/329293")



```
STOP: 0x00000050 Page_Fault_In_Non-Paged_Area Error After Installing Service Pack 1 (SP1)
View products that this article applies to.
Article ID	:	329293
Last Review	:	May 7, 2007
Revision	:	1.1
This article was previously published under Q329293
SYMPTOMS
When you restart your computer after you install Windows XP Service Pack 1 (SP1), your computer may generate the following Stop error message:
STOP: 0x00000050 (0x8872A990, 0x00000001, 0x804F35D7, 0x00000000)
PAGE_FAULT_IN_NON-PAGED_AREA
NOTE: The four parameters in this error message may vary according to the computer's configuration.

Back to the top
CAUSE
This problem may occur if there is a conflict between Windows XP SP1 and the display adapter drivers that are currently installed.

Back to the top
RESOLUTION
To resolve this problem, start your computer in Safe mode, remove the display adapter, rename the .inf files that are associated with the display adapter drivers, restart your computer in Normal mode, and then update your display adapter drivers. The following steps describe this procedure in more detail:
1.	Start Windows in Safe mode. To do so:
a. 	Restart the computer, and then press F8 while the computer starts.
b. 	On the Windows Advanced Options Menu that appears, use the ARROW keys to select Safe Mode, and then press ENTER.
c. 	Use the ARROW keys to select the operating system to start, and then press ENTER to start Windows XP in Safe mode.
2.	In the message that states that Windows is running in Safe mode, click Yes.
3.	Click Start, click Run, type msinfo32 in the Open box, and then click OK.
4.	Under System Summary, expand Components, and then click Display.
5.	In the right pane, note the information that corresponds to the INF File item, for example, Nv4.inf, Oem0.inf, or Atim128.inf.
6.	Quit the System Information utility.
7.	Click Start, right-click My Computer, and then click Properties.
8.	Click the Hardware tab, and then click Device Manager.
9.	Expand Display adapters, right-click the display adapter, and then click Uninstall.
10.	Click OK.
11.	Click Start, click Run, type cmd, and then click OK.
12.	In the Command Prompt window, type the following commands, and then press ENTER after each line:
ren %systemroot%\inf\INF file name from Step 5.inf *inf.old
ren %systemroot%\inf\INF file name from Step 5.pnf *pnf.old
13.	Close all open windows, and then restart the computer in the typical manner.
14.	Log on to Windows by using an account that has administrative privileges, and then wait for Windows to detect new hardware.
15.	When the Found New Hardware Wizard starts, click Cancel.

If you receive a stop error after you remove the updated display drivers, restart the computer and use the Last Known Good Configuration option. To do this, restart the computer, and then press the F8 key while the computer starts. On the Windows Advanced Options Menu that appears, use the ARROW keys to select Last Known Good Configuration, and then press ENTER.

If you receive a "System Has Recovered from a Serious Error" message when Windows starts, restart the computer again. This error message does not recur.
16.	Obtain and install the latest drivers for your display adapter.For information about how to contact computer hardware manufacturers, click the appropriate article number in the following list to view the article in the Microsoft Knowledge Base:
65416 (http://support.microsoft.com/kb/65416/EN-US/) Hardware and Software Third-Party Vendor Contact List, A-K

60781 (http://support.microsoft.com/kb/60781/EN-US/) Hardware and Software Third-Party Vendor Contact List, L-P

60782 (http://support.microsoft.com/kb/60782/EN-US/) Hardware and Software Third-Party Vendor Contact List, Q-Z

Back to the top
STATUS
Microsoft is researching this problem and will post more information in this article when the information becomes available.

Back to the top
MORE INFORMATION
For additional information, click the article numbers below to view the articles in the Microsoft Knowledge Base:
314466 (http://support.microsoft.com/kb/314466/EN-US/) Black Startup Screen Is Briefly Displayed, Computer Restarts Repeatedly
322389 (http://support.microsoft.com/kb/322389/EN-US/) How to Obtain the Latest Windows XP Service Pack

Back to the top
APPLIES TO
•	Microsoft Windows XP Professional
•	Microsoft Windows XP Home Edition

Back to the top
Keywords: 
	kbprb KB329293

Back to the top  
```

---

### Post by ddrichardson on 2007-07-22
Interesting, this is well worth reporting as a [bug]("http://www.ubuntu.com/community/ReportProblem"). I'm not overly familiar with file & settings transfer function however if something from your display settings is transferred it could well be what triggered the BSOD.

I've searched the previous bug reports and this is not filed.

---

