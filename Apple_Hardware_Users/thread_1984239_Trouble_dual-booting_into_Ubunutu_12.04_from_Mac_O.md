---
title: "Trouble dual-booting into Ubunutu 12.04 from Mac OSX 10.6.8"
date: 2012-05-21
forum: Apple Hardware Users
---

### Post by Coremiv on 2012-05-21
I'm trying to dual boot Ubuntu 12.04 from my existing Mac (as the title says, I'm running OSX 10.6.8), and I'm having some trouble.  I've referenced a few guides, but they give the same instructions as this one  [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I've got a partition set up (used to be a windows partition), rEFIt installed and working, but I can't get the next step working.  Whenever I try to boot using a CD or flashdrive I get this error message "No bootable device -- insert boot disk and press any key".

I've seen some other posts where people were successful with this sort of thing, and I'm hoping you guys can provide help.

---

### Post by Coremiv on 2012-05-22
Ok, I've been reading through
[http://ubuntuforums.org/showthread.php?t=1046568](http://ubuntuforums.org/showthread.php?t=1046568)
and
[http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)
but I'm still not having any luck.  Now the error I get when I try to use an Ubuntu boot disk is: Missing Operating System.  I've tried two different disks and a USB stick.  Any advice/help?

---

### Post by MarcoGuimaraes on 2012-05-22
[SIZE=2][COLOR=#000000][FONT=Helvetica, serif]if you have ubuntu installed and that is the problem try that :
in SL download and install -[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Helvetica, serif][ http://sourceforge.net/projects/gptfdisk/files/latest/downloa]("http://sourceforge.net/projects/gptfdisk/files/latest/downloa")[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Helvetica, serif] then run in terminal : sudo gdisk /dev/disk0
and choose the options : x - n - w .
reboot and when refit appear sync your disc and SHUT DOWN don't reboot, try enter in ubuntu .
if you are trying to install ubuntu don't use a usb, use a CD with 64bits version.
[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Helvetica, serif]:wink:[/FONT][/COLOR][/SIZE]

---

