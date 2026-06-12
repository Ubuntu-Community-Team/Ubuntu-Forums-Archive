---
title: "Kubuntu 7.10 Printers install will not print"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by OldLinuxGuy on 2008-01-26
This is my first post and it's the first time Linux has just kicked my butt.  I have access to two printers on this system they are 

HP Officejet T45 attached via LPT port Driver:  HP OfficeJet T45 Foomatic/hpijs (recommended) 

Brother 1440 on Windows machine connected via Samba.  Driver: Brother HL-1440 Foomatic/hl1250 (recommended)

The printers install fine using Add Printer from the KDE printing manager.  They even print the test page perfectly.  After that they no longer work even for the test page.  I get the following output: 

%! PS-Adobe-3.0 (NewLine) %% LanguageLevel: 1 (NewLine) %%DocumentData:  Clean7Bit (NewLine) %%DocumentSuppliedResou   

At this the printer is at the end of the page as the NewLine is without a Carriage Return.  The same output is on both printers.  So it does not appear to be a driver issue.  I am using the recommended drivers for both printers.  

My system is a AMD with Kubuntu 7.10 fresh install,  Cups version is 1.3.2

Can someone point me in the right direction?

Here is the Revelant portion of the error log.

E [26/Jan/2008:18:24:41 -0600] Pause-Printer: Unauthorized
I [26/Jan/2008:18:24:41 -0600] Saving printers.conf...
I [26/Jan/2008:18:24:41 -0600] Printer "Dave'sPrinter" stopped by "root".
I [26/Jan/2008:18:25:11 -0600] [Job 51] Adding start banner page "none".
I [26/Jan/2008:18:25:11 -0600] [Job 51] Adding job file of type application/postscript.
I [26/Jan/2008:18:25:11 -0600] [Job 51] Adding end banner page "none".
I [26/Jan/2008:18:25:11 -0600] [Job 51] Queued on "Dave'sPrinter" by "root".
I [26/Jan/2008:18:25:36 -0600] [Job 52] Adding start banner page "none".
I [26/Jan/2008:18:25:36 -0600] [Job 52] Adding job file of type application/postscript.
I [26/Jan/2008:18:25:36 -0600] [Job 52] Adding end banner page "none".
I [26/Jan/2008:18:25:36 -0600] [Job 52] Queued on "Dave'sPrinter" by "root".
I [26/Jan/2008:18:25:58 -0600] [Job 53] Adding start banner page "none".
I [26/Jan/2008:18:25:58 -0600] [Job 53] Adding job file of type application/postscript.
I [26/Jan/2008:18:25:58 -0600] [Job 53] Adding end banner page "none".
I [26/Jan/2008:18:25:58 -0600] [Job 53] Queued on "Pat'sPrinter" by "root".
I [26/Jan/2008:18:25:58 -0600] [Job 53] Started filter /usr/lib/cups/filter/pstops (PID 9318)
I [26/Jan/2008:18:25:58 -0600] [Job 53] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9319)
I [26/Jan/2008:18:25:58 -0600] [Job 53] Started backend /usr/lib/cups/backend/smb (PID 9320)
I [26/Jan/2008:18:25:59 -0600] [Job 53] Completed successfully.
E [26/Jan/2008:18:27:08 -0600] Resume-Printer: Unauthorized
I [26/Jan/2008:18:27:08 -0600] Saving printers.conf...
I [26/Jan/2008:18:27:08 -0600] Printer "Dave'sPrinter" started by "root".
I [26/Jan/2008:18:27:08 -0600] [Job 51] Started filter /usr/lib/cups/filter/pstops (PID 9330)
I [26/Jan/2008:18:27:08 -0600] [Job 51] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9331)
I [26/Jan/2008:18:27:08 -0600] [Job 51] Started backend /usr/lib/cups/backend/hp (PID 9332)
I [26/Jan/2008:18:27:24 -0600] [Job 51] Completed successfully.


I [26/Jan/2008:18:27:24 -0600] [Job 52] Started filter /usr/lib/cups/filter/pstops (PID 9341)
I [26/Jan/2008:18:27:24 -0600] [Job 52] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9342)
I [26/Jan/2008:18:27:24 -0600] [Job 52] Started backend /usr/lib/cups/backend/hp (PID 9343)
I [26/Jan/2008:18:27:39 -0600] [Job 52] Completed successfully.
I [26/Jan/2008:18:54:28 -0600] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=9751)
I [26/Jan/2008:18:54:48 -0600] Started "/usr/lib/cups/cgi-bin/help.cgi" (pid=9752)
I [26/Jan/2008:18:54:59 -0600] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=9753)

---

### Post by OldLinuxGuy on 2008-01-29
Well here is some futher information for reference.  It appears to be a problem with foomatic and ghostscript I'm getting the unknown option error on an expanded error log.  Will this get me some assistance?  So far I'm underwhelmed.

---

### Post by jemdos on 2008-01-29
Greetings from sunny Spain 8)

I've the very same problem with a Kyocera FS-600. Foomatic drivers (or windows PPD from the printer's CD) did not work. But a Gutenprint driver (under CUPS) I found toying with the available ubuntu drivers works perfectly in my system.

I'd advise to try it out one for your printer. Look in Synaptic for Gutenprint packages. 

Hope it helps.

---

### Post by OldLinuxGuy on 2008-01-29
Greetings thanks for your response here in Windy Snowy Chicago USA it is a nice -14 Deg/C.  I tried the other drivers and downloading a few more but it's all no go it either gives me the same result or locks my system.  I need some sleep, time for bed with OldWindowsGirl who oddly enough can use the printers no problem,

---

### Post by iansane on 2008-01-30
I have a Brother mfc6800 and I could not find a gutenprint driver for it. Had to go with what Brother has for linux drivers and it was a real pain.

---

### Post by OldLinuxGuy on 2008-01-30
Well I got it to work but not sure how.  I used the HPLIP Toolbox found under the system menu and it works.  Same driver and everything.  Looks like there are some bugs in the printer installation routines.  Thanks for responses.

---

