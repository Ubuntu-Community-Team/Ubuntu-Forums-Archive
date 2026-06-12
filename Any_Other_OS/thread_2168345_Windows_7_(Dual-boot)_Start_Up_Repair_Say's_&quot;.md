---
title: "Windows 7 (Dual-boot) Start Up Repair Say's &quot;System Volume Is Corrupt&quot;"
date: 2013-08-17
forum: Any Other OS
---

### Post by jeffroaltiere1 on 2013-08-17
[COLOR=#323232][FONT=verdana]I recently bought and ins[/FONT][/COLOR][COLOR=#323232][FONT=verdana]talled Windows 7 Home Premium OEM onto my HP G42 (which is now 2.5 years old). I had Win 7 home Premium on it when I bought it, but the hard drive broke and I ended up getting a new drive (Seagate Momentus 7200 750 GB 7200RPM SATA 3Gb/s 16 MB Cache). I installed it onto there, and it seemed to be working fine for a few start ups. Then when I tried doing an update, I got blue screened the when rebooting, and it wouldn't let me back in. [/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]From there, I decided to completely re-install Win 7 (I really had nothing of value on there), and that worked longer. It still had trouble doing an update, but after trying it again, it worked fine. It was a few days ago that it began giving me blue screens telling me a "critical system process has stopped working or terminated". Now, when I try booting to it, it will get to the start up screen with the animation, then it'll reboot after a minute and tell me it had trouble booting.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]I ran start up repair, and it told me that the root cause was that the system volume was corrupt. I'm not really sure of what I can do now. Is there any way to fix this problem or to prevent it from happening in the future? [/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Side note: I don't know if any of you are proficient in the Ubuntu system (I dual-boot with ubuntu 13.04), but I tried accessing the Win 7 partition from there and it gave me this message (see attachment):
[/FONT][/COLOR][ATTACH=CONFIG]245440[/ATTACH]

---

### Post by oldfred on 2013-08-17
That most often just means you need to use your Windows repairCD or flash drive to run chkdsk. But it could be that you were hibernating Windows and after dual booting and maybe writing something from Ubuntu into the NTFS partition has corrupted the hiberfile.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by jeffroaltiere1 on 2013-08-18
I don't ever put it into Hibernate. I only lock it or I completely shut it down. I did run```
chkdsk
``` though, and it gave me this. Also, it said my system was in D:, which is odd because it should be in C:

---

### Post by jeffroaltiere1 on 2013-08-18
I was told to run```
chkdsk c: /r
``` over on Seven Forums. I ran it, and I pretty much came out with the same results as before.[ATTACH=CONFIG]245466[/ATTACH]

---

### Post by oldfred on 2013-08-18
Do you still get the mount error?

---

### Post by jeffroaltiere1 on 2013-08-19
Yes. As stated before, I will boot into Windows, get the animation, then it shut down, and start back up again.

---

### Post by jeffroaltiere1 on 2013-08-19
Okay, so I ran ```
chkdsk d: /r
``` a few hours later, it finished. Here's the results from that.

[ATTACH=CONFIG]245495[/ATTACH]

I rebooted, and it started successfully. I was able to get in, and  nothing seemed wrong. Then, I got a blue screen that told me a "crucial  system process had been terminated or stopped working". It rebooted, and  came to this.

*Black Screen that reads "SMART DISK ERROR PLEASE RUN HARD DISK TEST"*

I rebooted after that, but it wouldn't start then. So, I ran Startup Repair, and it gave me this.

[ATTACH=CONFIG]245494[/ATTACH] *Reads: Registry is corrupt*

So, I rebooted, and it came back up successfully. I've been noticing  that over the many times this has happened to me, Windows Aero has been  effected by this. It keeps turning off. It will just give me the sky  blue solid bar at the bottom of my screen. It's after I change it though  that eventually something goes wrong. Could this be part of the  problem? A problem with Aero?

*Sidenote: I know the pictures are upside down. I tried editing them, then I re-uploaded them. They still won't change.*

---

### Post by oldfred on 2013-08-20
I am not familar with Aero. But Smart Disk is a tool to check hard drive.

Verify that disk is not developing issues by going into Disks or Disk utility and click on drive. On right side is Smart status. All I really know is passed or green is good. It can run a lot of tests.

---

### Post by jeffroaltiere1 on 2013-08-25
For more on this happy mess of mine, check my post on Seven Forums. [http://www.sevenforums.com/hardware-devices/301503-windows-7-start-up-repair-says-system-volume-corrupt.html](http://www.sevenforums.com/hardware-devices/301503-windows-7-start-up-repair-says-system-volume-corrupt.html)

---

