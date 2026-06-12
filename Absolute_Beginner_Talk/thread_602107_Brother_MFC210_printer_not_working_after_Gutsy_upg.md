---
title: "Brother MFC210 printer not working after Gutsy upgrade"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-11-03
My Brother MFC 210C Brother printer was working fine on Feisty, but after the upgrade to Gutsy it stopped working. I followed post: [http://ubuntuforums.org/showthread.php?p=3671326#post3671326](http://ubuntuforums.org/showthread.php?p=3671326#post3671326)
Still the same thing - I try the test page and nothing, Just states printer is idle.
Under System - Admin- printing the MFC210 shows, I have it as default but nothing.
Below is my Cups error log - pretty much a newbie and would appreciate any help.
Previous posts apply to use with Feisty and I found only 1 post referring to Gutsy (above) that didn't work.


E [03/Nov/2007:18:47:06 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [03/Nov/2007:21:47:23 +0000] Pause-Printer: Unauthorized
E [03/Nov/2007:21:48:54 +0000] CUPS-Set-Default: Unauthorized
E [03/Nov/2007:21:52:50 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [03/Nov/2007:21:52:50 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [03/Nov/2007:21:53:17 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [03/Nov/2007:21:53:17 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [03/Nov/2007:21:53:33 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [03/Nov/2007:21:54:49 +0000] Pause-Printer: Unauthorized
E [03/Nov/2007:21:55:13 +0000] Resume-Printer: Unauthorized
E [03/Nov/2007:21:56:05 +0000] cupsdAuthorize: Local authentication certificate not found!
E [03/Nov/2007:21:56:05 +0000] Pause-Printer: Unauthorized
E [03/Nov/2007:21:57:22 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [03/Nov/2007:21:57:22 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [03/Nov/2007:22:03:00 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [03/Nov/2007:22:03:01 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [04/Nov/2007:01:38:23 +0000] CUPS-Delete-Printer: Unauthorized
E [04/Nov/2007:01:42:28 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:01:43:40 +0000] CUPS-Set-Default: Unauthorized
E [04/Nov/2007:01:44:18 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [04/Nov/2007:01:44:18 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [04/Nov/2007:01:44:42 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:01:45:02 +0000] CUPS-Set-Default: Unauthorized
E [04/Nov/2007:01:49:19 +0000] Pause-Printer: Unauthorized
E [04/Nov/2007:01:50:03 +0000] Resume-Printer: Unauthorized
E [04/Nov/2007:01:51:12 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:01:51:12 +0000] PID 9756 (/usr/lib/cups/backend/usb) crashed on signal 9!
E [04/Nov/2007:01:52:29 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:01:52:29 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:01:52:34 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:01:52:34 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:01:57:45 +0000] CUPS-Delete-Printer: Unauthorized
E [04/Nov/2007:02:00:40 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:02:02:05 +0000] Pause-Printer: Unauthorized
E [04/Nov/2007:02:02:16 +0000] CUPS-Delete-Printer: Unauthorized
E [04/Nov/2007:02:03:32 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:02:04:21 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [04/Nov/2007:02:04:21 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [04/Nov/2007:02:04:26 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:02:06:30 +0000] CUPS-Delete-Printer: Unauthorized
E [04/Nov/2007:02:08:22 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [04/Nov/2007:02:08:22 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [04/Nov/2007:02:08:27 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:02:08:53 +0000] CUPS-Set-Default: Unauthorized
E [04/Nov/2007:02:09:39 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [04/Nov/2007:02:09:39 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [04/Nov/2007:02:09:47 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [04/Nov/2007:02:09:47 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [04/Nov/2007:02:13:15 +0000] Filter "brlpdwrapperMFC210C" for printer "MFC-210C" not available: No such file or directory
E [04/Nov/2007:02:13:15 +0000] Filter "brlpdwrapperMFC210C" for printer "MFC-210C" not available: No such file or directory
E [04/Nov/2007:02:13:19 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [04/Nov/2007:02:21:49 +0000] Pause-Printer: Unauthorized
E [04/Nov/2007:02:22:03 +0000] CUPS-Delete-Printer: Unauthorized
E [04/Nov/2007:02:22:22 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:02:22:22 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:02:22:22 +0000] cupsdAuthorize: Local authentication certificate not found!
E [04/Nov/2007:02:22:22 +0000] cupsdAuthorize: Local authentication certificate not found!

---

### Post by trjonescp on 2007-11-04
I'm having the same problem (Brother printer, Gutsy 7.10, same looking error log), although I am setting up my Brother DCP7020 printer for the first time. Any advice would be greatly appreciated!

---

### Post by Tony3286 on 2007-11-04
Well I finally got the Brother printer to work. From what I understand , you don't need the
LPR driver with Gutsy. I had previously use BobSongs post: [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703) (steps 1,2, the first 2 lines in step 3 and in Step 4 the first line. I went to  Brother website and download the Debain CUPS **Wrapper only**  to my desktop.  I then, as I did previously under Feisty, used Killtowns script - [http://ubuntuforums.org/showpost.php?p=2925204&postcount=12](http://ubuntuforums.org/showpost.php?p=2925204&postcount=12).
I download his script to my desktop, as he instructs and followed his steps 1-6. God knows why it worked, but it did. The Brother MFC210C now works like it did in Feisty.

---

### Post by Tommy on 2007-11-05
> **trjonescp said:**
> I'm having the same problem (Brother printer, Gutsy 7.10, same looking error log), although I am setting up my Brother DCP7020 printer for the first time. Any advice would be greatly appreciated!

My DCP7020 was working with the Brother drivers in Edgy 6.10 and Feisty 7.04 but Gutsy 7.10 killed it. I'm not sure what all the installer recommended in this thread is doing, but for now I have my printer going with the information from here [http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020](http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020)

Choose the HL1250 driver and it will work OK. I will keep trying to figure out how to get the Brother driver going because it has a few more features and probably higher quality.

(The Brother scanner driver is working fine, but I haven't tried their scanner buttons driver yet. They've upgraded all the packages since I first downloaded everything.)

---

