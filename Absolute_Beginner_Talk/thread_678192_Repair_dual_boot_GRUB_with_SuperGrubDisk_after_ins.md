---
title: "Repair dual boot GRUB with SuperGrubDisk after install"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by gritz_1 on 2008-01-25
I have a PC with 2-160G SATA HDs; HBA1 (0) has Windows XP Pro installed, and last night I installed Ubuntu 7.10 on HBA2 (1). I let Ubuntu set up the GRUB loader on the MBR on HBA1. The installation went fine. When I rebooted, I got the GRUB loader screen (with 2 Windows XP Professional lines, see below). I selected the Ubuntu 7.10 OS and all I got was a screen that said "Starting..." and I had to force a restart. I then selected the Microsoft Windows XP Professional (#1) and got the error message;
"Windows could not start because the following file is missing or corrupt. 
<windows root>\system32\ntoskrnl.exe" and I had to force a restart.
I then selected the Microsoft Windows XP professional (#2) and that file with a different file error message and I was forced to restart. 
I booted with the SuperGrubDisk and was able to start Windows XP (no problem) and then tried Ubuntu (no problem) so the OSes are good. 
I read through the help files on the SuperGrubDisk CD and my question, before I start a repair, is this; which fix or fixes should I be looking at to resolve this issue? I did not want try and guess which ones were correct. The MBR seems okay because it does bring up GRUB as I would expect. I see the correct choices in GRUB (expect for the phantom Windows XP Pro, but I did have an external USB drive plugged in during Ubuntu the install, shame on me). 
So this seems like a "simple" fix, but being a novice to Ubuntu and GRUB, I sure would love some help.

---

### Post by dcstar on 2008-01-25
> **gritz_1 said:**
> I have a PC with 2-160G SATA HDs; HBA1 (0) has Windows XP Pro installed, and last night I installed Ubuntu 7.10 on HBA2 (1). I let Ubuntu set up the GRUB loader on the MBR on HBA1. The installation went fine. When I rebooted, I got the GRUB loader screen (with 2 Windows XP Professional lines, see below). I selected the Ubuntu 7.10 OS and all I got was a screen that said "Starting..." and I had to force a restart. I then selected the Microsoft Windows XP Professional (#1) and got the error message;
"Windows could not start because the following file is missing or corrupt. 
<windows root>\system32\ntoskrnl.exe" and I had to force a restart.
I then selected the Microsoft Windows XP professional (#2) and that file with a different file error message and I was forced to restart. 
I booted with the SuperGrubDisk and was able to start Windows XP (no problem) and then tried Ubuntu (no problem) so the OSes are good. 
I read through the help files on the SuperGrubDisk CD and my question, before I start a repair, is this; which fix or fixes should I be looking at to resolve this issue? I did not want try and guess which ones were correct. The MBR seems okay because it does bring up GRUB as I would expect. I see the correct choices in GRUB (expect for the phantom Windows XP Pro, but I did have an external USB drive plugged in during Ubuntu the install, shame on me). 
So this seems like a "simple" fix, but being a novice to Ubuntu and GRUB, I sure would love some help.

Do a forum search for "reinstall grub".

---

### Post by LaRoza on 2008-01-25
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by gritz_1 on 2008-01-25
Would I reinstall GRUB if it appears and the boot loader menu comes up? True, it does not work to boot the systems, but if it's already there, would reinstalling repair it or leave me in the same position?

---

### Post by gritz_1 on 2008-01-26
Tried the GRUB reinstall three times; verified all the parameters and bios settings per all the posts I found in the forums. I get the same results each time. Ubuntu will boot maybe one out of 15 times, but it usually hangs at "Starting up...". Windows will not boot, and gives the aformentioned error message each time it is selected. I am stumped. I do not get GRUB errors. I know the GRUB is installed on the correct MBR and the boot BIOS order is correct. Any thoughts or further troubleshooting techniques woould be helpful. I went so far as to try the NT booloader method. This boots XP fine, but when I select UBUNTU after adding the boosect.lnx, etc and adding the .lnx from Ubuntu, the sysem just gives me a cursor...taunting me...

---

