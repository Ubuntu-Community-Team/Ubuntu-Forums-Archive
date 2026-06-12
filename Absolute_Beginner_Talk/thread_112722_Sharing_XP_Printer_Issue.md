---
title: "Sharing XP Printer Issue"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Harimwakairi on 2006-01-04
I'm attempting to get the HP DeskJet 3650 attached to my WinXP desktop to accept jobs from my HP dv1227 on which I've just installed Ubuntu 5.10.  I have searched the forums for help but not found anything that discusses this specific problem.

I started by following the SMB instructions found in the user documentation and wiki.  I have file sharing working over SMB just fine, so I figured that would be the way to do it.  I used System->Administration->Printers to add a printer to Ubuntu.  It detected the printer just fine, provided a driver, and made a little icon for me in the printers dialog.  

When I attempted to print a test page, the printer made its usual noises, but the stopped and failed to print anything.  I opened the print queue on my Windows Box and saw that it had received a job but was stuck somehow, saying the job was "Printing", and that the size was "64.0 KB/7.24 MB".

I cancelled that job (which required a reboot of my XP machine to remove from the queue) and tried again using these instructions:

[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html]("http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html")

Again the dialog created a little printer icon for me, I again tried a test page.  This time I had the queue open to watch what happened.  It showed the job spooling (size went from 0 to 7.42 MB).  IT then switch to "Printing", and the job locked at 64.0 KB of 7.42 MB.  The printer made some noises and shifted around but didn't print anything.

I then tried these instructions:

[https://wiki.ubuntu.com/WindowsXPPrinter]("https://wiki.ubuntu.com/WindowsXPPrinter")

But that didn't help either.

At this point I'm not sure what to try.  I've searched the net and these forums but can't find anything that seems to address this issue.  This isn't a particularly new printer, so I wouldn't think it's an old driver issue.  It works fine under XP, and is listed as compatible with Linux in the HCL.

---

### Post by tim15856 on 2006-01-05
I found this in a troubleshooting section. It's for Debian, so it should apply to Ubuntu.

Other failures include being unable to print to a local printer and having your print jobs disappear from the
queue without being printed. You may also see vague error messages such as Child process 2384
exited with status 32.
Increase CUPS' logging level to "debug" to see more messages about what happened before the print job
failed.
Open the main CUPS configuration file /etc/cups/cupsd.conf in a text editor.
1. 
Change the line that reads "LogLevel warn" to "LogLevel debug".
2. 
Save the configuration file and exit the text editor.
3. 
Restart the CUPS server with the command:
/etc/init.d/cupsys restart
4. 
You can follow the CUPS log with the following command:
/usr/bin/tail &#8722;f /var/log/cups/error_log
You should see a line that reads Scheduler shutting down due to SIGTERM. This indicates that
the CUPS server was stopped successfully.
Send your print job again and watch for useful debug messages that appear. One example of a useful debug
message is GNU Ghostscript 7.05: Can't start ijs server 'hpijs'. In this case the
solution is to install the "hpijs" package

---

### Post by Harimwakairi on 2006-01-05
Thanks for the help.   hve done as you suggested, changing the error logging to debug level and restarting cups.  I tried the process over again, deleting the printer registration from my ubuntu laptop and making it again using SMB.  I used my windows box's hostname for the host, it autofilled the dropdown for printer selection with the correct name of my shared printer, and I used my windows login and password as the "user" and "password" fields that the new printer dialog takes.

I then tried printing a test page and then went and looked at the logs.  I found it was mostly lines that seemed to indicate the daemon was checking to see if it had anything to do.  There were two interesting sections, however:

> D [05/Jan/2006:01:28:47 -0500] AcceptClient: 6 from localhost:631.
D [05/Jan/2006:01:28:47 -0500] ReadClient: 6 POST /admin/ HTTP/1.1
I [05/Jan/2006:01:28:47 -0500] Setting DeskJet-3650 device-uri to "smb://EIGHTSQUARED/deskjet" (was "file:/dev/null".)
I [05/Jan/2006:01:28:47 -0500] Setting DeskJet-3650 printer-is-accepting-jobs to 1 (was 0.)
I [05/Jan/2006:01:28:47 -0500] Setting DeskJet-3650 printer-state to 3 (was 5.)
D [05/Jan/2006:01:28:47 -0500] add_printer: Copied PPD file successfully!
I [05/Jan/2006:01:28:47 -0500] Saving printers.conf...
I [05/Jan/2006:01:28:47 -0500] New printer 'DeskJet-3650' added by 'root'.
D [05/Jan/2006:01:28:47 -0500] ProcessIPPRequest: 6 status_code=0
D [05/Jan/2006:01:28:47 -0500] CloseClient: 6

The above appears to be the response from my registration of the printer.

> D [05/Jan/2006:01:29:09 -0500] AcceptClient: 6 from localhost:631.
D [05/Jan/2006:01:29:09 -0500] ReadClient: 6 POST /printers/DeskJet-3650 HTTP/1.1
D [05/Jan/2006:01:29:09 -0500] print_job: auto-typing file...
D [05/Jan/2006:01:29:09 -0500] print_job: request file type is application/postscript.
D [05/Jan/2006:01:29:09 -0500] check_quotas: requesting-user-name = 'andrew'
D [05/Jan/2006:01:29:09 -0500] print_job: requesting-user-name = 'andrew'
D [05/Jan/2006:01:29:09 -0500] Adding default job-sheets values "none,none"...
I [05/Jan/2006:01:29:09 -0500] Adding start banner page "none" to job 9.
I [05/Jan/2006:01:29:09 -0500] Adding end banner page "none" to job 9.
I [05/Jan/2006:01:29:09 -0500] Job 9 queued on 'DeskJet-3650' by 'andrew'.
D [05/Jan/2006:01:29:09 -0500] Job 9 hold_until = 0
D [05/Jan/2006:01:29:09 -0500] StartJob(9, 0x8094458)
D [05/Jan/2006:01:29:09 -0500] StartJob() id = 9, file = 0/1
D [05/Jan/2006:01:29:09 -0500] job-sheets=none,none
D [05/Jan/2006:01:29:09 -0500] banner_page = 0
D [05/Jan/2006:01:29:09 -0500] StartJob: argv = "DeskJet-3650","9","andrew","Test Page","1","","/var/spool/cups/d00009-001"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[2]="USER=root"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[3]="CHARSET=utf-8"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[4]="LANG=en_US"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[5]="TZ=US/Eastern"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[6]="PPD=/etc/cups/ppd/DeskJet-3650.ppd"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[11]="DEVICE_URI=smb://EIGHTSQUARED/deskjet"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[12]="PRINTER=DeskJet-3650"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[15]="CUPS_SERVER=localhost"
D [05/Jan/2006:01:29:09 -0500] StartJob: envp[16]="IPP_PORT=631"
D [05/Jan/2006:01:29:09 -0500] StartJob: statusfds = [ 7 8 ]
D [05/Jan/2006:01:29:09 -0500] StartJob: filterfds[1] = [ 9 -1 ]
D [05/Jan/2006:01:29:09 -0500] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [05/Jan/2006:01:29:09 -0500] StartJob: filterfds[0] = [ 10 11 ]
D [05/Jan/2006:01:29:09 -0500] start_process("/usr/lib/cups/filter/pstops", 0xbfda7790, 0xbfda6d08, 9, 11, 8)
I [05/Jan/2006:01:29:09 -0500] Started filter /usr/lib/cups/filter/pstops (PID 17282) for job 9.
D [05/Jan/2006:01:29:09 -0500] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [05/Jan/2006:01:29:09 -0500] StartJob: filterfds[1] = [ 9 12 ]
D [05/Jan/2006:01:29:09 -0500] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbfda7790, 0xbfda6d08, 10, 12, 8)
I [05/Jan/2006:01:29:09 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 17283) for job 9.
D [05/Jan/2006:01:29:09 -0500] StartJob: backend = "/usr/lib/cups/backend/smb"
D [05/Jan/2006:01:29:09 -0500] StartJob: filterfds[0] = [ -1 10 ]
D [05/Jan/2006:01:29:09 -0500] start_process("/usr/lib/cups/backend/smb", 0xbfda7790, 0xbfda6d08, 9, 10, 8)
I [05/Jan/2006:01:29:09 -0500] Started backend /usr/lib/cups/backend/smb (PID 17284) for job 9.
D [05/Jan/2006:01:29:09 -0500] ProcessIPPRequest: 6 status_code=0
D [05/Jan/2006:01:29:09 -0500] [Job 9] perl: warning: Setting locale failed.
D [05/Jan/2006:01:29:09 -0500] [Job 9] perl: warning: Please check that your locale settings:
D [05/Jan/2006:01:29:09 -0500] [Job 9] LANGUAGE = (unset),
D [05/Jan/2006:01:29:09 -0500] [Job 9] LC_ALL = (unset),
D [05/Jan/2006:01:29:09 -0500] [Job 9] LANG = "en_US"
D [05/Jan/2006:01:29:09 -0500] [Job 9] are supported and installed on your system.
D [05/Jan/2006:01:29:09 -0500] [Job 9] perl: warning: Falling back to the standard locale ("C").
D [05/Jan/2006:01:29:09 -0500] [Job 9] Page = 612x792; 18,36 to 594,783
D [05/Jan/2006:01:29:09 -0500] [Job 9] slowcollate=0, slowduplex=0, sloworder=0
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%Title: PPR Test Page
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%Pages: 1
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%DocumentNeededResources: font Helvetica
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%EndComments
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%BeginProlog
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%EndProlog
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%BeginSetup
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%IncludeResource: font Helvetica
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%IncludeFeature: *PageSize Letter
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%EndSetup
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%Page: 1 1
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%Page: 1 1
D [05/Jan/2006:01:29:09 -0500] [Job 9] pw = 576.0, pl = 747.0
D [05/Jan/2006:01:29:09 -0500] [Job 9] PageLeft = 18.0, PageRight = 594.0
D [05/Jan/2006:01:29:09 -0500] [Job 9] PageTop = 783.0, PageBottom = 36.0
D [05/Jan/2006:01:29:09 -0500] [Job 9] PageWidth = 612.0, PageLength = 792.0
D [05/Jan/2006:01:29:09 -0500] [Job 9] 0 %%BeginDocument: /home/jdub/Documents/Canonical/Logos/Ubuntu_logo.eps
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%Title: Ubuntu final logo
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%Creator: FreeHand 10.0
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%CreationDate: 15/9/04 11:16 am
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%BoundingBox: 0 0 350 81
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%FHPathName:Work:CANONICAL SOFTWARE:Ubuntu:UBUNTU Identity:Ubuntu final logo
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%FHPageNum:1
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%DocumentSuppliedResources: procset Altsys_header 4 0
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%ColorUsage: Color
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%DocumentProcessColors: Black
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%DocumentCustomColors: (PANTONE 2965 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (PANTONE 151 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (PANTONE 1235 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (PANTONE 179 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (0r 43g 61b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (244r 72g 0b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (251r 139g 0b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ (212r 0g 0b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%CMYKCustomColor: 1 0.38 0 0.69 (PANTONE 2965 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0 0.43 0.87 0 (PANTONE 151 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0 0.275 0.76 0 (PANTONE 1235 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0 0.79 0.94 0 (PANTONE 179 CVC)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0.7613 0.5271 0.6244 0.7124 (0r 43g 61b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0.0017 0.7251 0.8508 0 (244r 72g 0b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0.0032 0.4248 0.8274 0 (251r 139g 0b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%+ 0.0176 0.9327 0.9184 0 (212r 0g 0b)
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%EndComments
D [05/Jan/2006:01:29:09 -0500] [Job 9] 1 %%BeginFont: Times-Roman
D [05/Jan/2006:01:29:10 -0500] [Job 9] foomatic-rip version $Revision: 3.43.2.11 $ running...
D [05/Jan/2006:01:29:10 -0500] [Job 9] Parsing PPD file ...
D [05/Jan/2006:01:29:10 -0500] [Job 9] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option ColorSpace
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option Resolution
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option PageSize
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option PageRegion
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option Model
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option PrintoutMode
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option ImageableArea
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option PaperDimension
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option Quality
D [05/Jan/2006:01:29:10 -0500] [Job 9] Added option Font
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] Parameter Summary
D [05/Jan/2006:01:29:10 -0500] [Job 9] -----------------
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] Spooler: cups
D [05/Jan/2006:01:29:10 -0500] [Job 9] Printer: DeskJet-3650
D [05/Jan/2006:01:29:10 -0500] [Job 9] PPD file: /etc/cups/ppd/DeskJet-3650.ppd
D [05/Jan/2006:01:29:10 -0500] [Job 9] Printer model: HP DeskJet 3650 Foomatic/hpijs (recommended)
D [05/Jan/2006:01:29:10 -0500] [Job 9] Job title: Test Page
D [05/Jan/2006:01:29:10 -0500] [Job 9] File(s) to be printed: 
D [05/Jan/2006:01:29:10 -0500] [Job 9] <STDIN>
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] ================================================
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] File: <STDIN>
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] ================================================
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] Reading PostScript input ...
D [05/Jan/2006:01:29:10 -0500] [Job 9] --> This document is DSC-conforming!
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] -----------
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%BeginProlog
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%EndProlog
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] -----------
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%BeginSetup
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%BeginFeature: *PrintoutMode Normal
D [05/Jan/2006:01:29:10 -0500] [Job 9] Option: PrintoutMode=Normal --> Setting option
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [05/Jan/2006:01:29:10 -0500] [Job 9] Option: PrintoutMode=Normal --> Setting option
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%BeginFeature: *Quality FromPrintoutMode
D [05/Jan/2006:01:29:10 -0500] [Job 9] Option: Quality=FromPrintoutMode --> Setting option
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [05/Jan/2006:01:29:10 -0500] [Job 9] Option: Quality=FromPrintoutMode --> Setting option
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%BeginFeature: *PageSize Letter
D [05/Jan/2006:01:29:10 -0500] [Job 9] Option: PageSize=Letter --> Setting option
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %% FoomaticRIPOptionSetting: PageSize=Letter
D [05/Jan/2006:01:29:10 -0500] [Job 9] Option: PageSize=Letter --> Setting option
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%EndSetup
D [05/Jan/2006:01:29:10 -0500] [Job 9] Inserting PostScript code for CUPS' page accounting
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] -----------
D [05/Jan/2006:01:29:10 -0500] [Job 9] New page:  1 1
D [05/Jan/2006:01:29:10 -0500] [Job 9] Inserting option code into "PageSetup" section.
D [05/Jan/2006:01:29:10 -0500] [Job 9] No page header or page header not DSC-conforming
D [05/Jan/2006:01:29:10 -0500] [Job 9] Stopping search for page header options
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found:
D [05/Jan/2006:01:29:10 -0500] [Job 9] 66BA0F2FBD4C92D25121A2647E8081BF05241DF408C9CE4EED2A630C3018869E51E7F90C030031A6E8FEE178DF9A598A4F1D8CA4C7741AA2C40081C0D48C29A8B4B60A0FE5D7BA4DD1F7CC51282CEF697AC70713546B0933B65246AAAC6A881DFB16
D [05/Jan/2006:01:29:10 -0500] [Job 9] --> Output goes directly to the renderer now.
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] Starting renderer
D [05/Jan/2006:01:29:10 -0500] [Job 9] JCL: <job data> 
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] renderer PID kid4=17288
D [05/Jan/2006:01:29:10 -0500] [Job 9] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 3600" -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1 -dIjsUseOutputFD -sOutputFile=- -
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%EndFont
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%BeginResource: procset Altsys_header 4 0
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%EndResource
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%EndProlog
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%BeginSetup
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%IncludeResource: font Times-Roman
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%EndSetup
D [05/Jan/2006:01:29:10 -0500] [Job 9] perl: warning: Setting locale failed.
D [05/Jan/2006:01:29:10 -0500] [Job 9] perl: warning: Please check that your locale settings:
D [05/Jan/2006:01:29:10 -0500] [Job 9] LANGUAGE = (unset),
D [05/Jan/2006:01:29:10 -0500] [Job 9] LC_ALL = (unset),
D [05/Jan/2006:01:29:10 -0500] [Job 9] LANG = "en_US"
D [05/Jan/2006:01:29:10 -0500] [Job 9] are supported and installed on your system.
D [05/Jan/2006:01:29:10 -0500] [Job 9] perl: warning: Falling back to the standard locale ("C").
D [05/Jan/2006:01:29:10 -0500] [Job 9] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 3600' '-dDEVICEWIDTHPOINTS=612' '-dDEVICEHEIGHTPOINTS=792' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%Trailer
D [05/Jan/2006:01:29:10 -0500] [Job 9] 1 %%EndDocument
D [05/Jan/2006:01:29:10 -0500] [Job 9] 0 %%Trailer
D [05/Jan/2006:01:29:10 -0500] [Job 9] Saw Trailer!
D [05/Jan/2006:01:29:10 -0500] [Job 9] Saw EOF!
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%EndProlog
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] -----------
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%BeginSetup
D [05/Jan/2006:01:29:10 -0500] [Job 9] "%%BeginSetup" in page header
D [05/Jan/2006:01:29:10 -0500] [Job 9] Found: %%EndSetup
D [05/Jan/2006:01:29:10 -0500] [Job 9] 
D [05/Jan/2006:01:29:10 -0500] [Job 9] Closing renderer


That appears to be the log from the test page I printed.  It doesn't seem to contain any error messages, though it does have a warning about some type of locale setting.  After reading this I went and checked my windows logs in the management console, but they don't show anything about the printer.

This is frustrating.  :(

---

### Post by Harimwakairi on 2006-01-05
I have found the solution to my problem.  By turning off bi-directional support in the printer properties on my windows box, I got the printer to work.  I imagine the printer driver was trying to send some data back to the Linux machine and failing, causing it to hang.  Anyway, thought I'd post my findings here so that if someone else runs into this issue they'll find this post with the search form.

---

### Post by tim15856 on 2006-01-05
Glad to see you figured it out. That's good to know.

---

### Post by Tuf on 2006-01-05
I am having the same problem except my printer is local and installed on the USB bus.  I dont think there is any bi-directional settings for USB.  

It worked until I updated KDE this morning :/

---

