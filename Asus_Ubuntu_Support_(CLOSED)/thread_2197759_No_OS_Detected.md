---
title: "No OS Detected"
date: 2014-01-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by asengpeace on 2014-01-05
Hello Folks,

This is my first time changing my OS into linux family,,but i have a few problem during the installation, I am getting the message: "This computer currently has no  detected operating systems. What would you like to do?". Windows 8 (Windows 8.1 Pro Preview) is  installed on the computer and works, but is not being detected by Ubuntu.

I am using a pen drive and installing Ubuntu 13.04 ,my laptop brand Asus.

please help.thanks

---

### Post by validust on 2014-01-05
Hi asengpeace! If you want to keep the windows-OS, it should be possible to open gparted in the live-ubuntu (Maybe you would have to download gparted.), and rezise it -shrink it.  Then, create a partition for ubuntu, ext4, maybe. When you thereafter start the installer, there ought to be an option, following the question "What would you like to do?", to install to that partition.

---

### Post by asengpeace on 2014-01-05
i want to make a clean install on my system without deleting the whole data on other partiiton

---

### Post by Bucky Ball on 2014-01-05
NO! Don't use Ubuntu software to resize the Win8 partition. That can serious scramble your system and boot. You need to use Win software to do that so boot into Win if you want to resize that partition or defrag it. Rule of thumb: Win software for resizing Win partition, *buntu for *buntu partitions.

Welcome to the forums. If you're booting Win8 then EFI is probably the issue. You HAVE to boot Ubuntu in UEFI mode as well or it won't detect Win8. In the BIOS, make sure you are booting in EFI. In there, just make sure that the Win8 is also booting EFI (it should be marked that way). 

Is Win8 preinstalled or did you install it yourself? If it was pre-installed this presents other issues. You need to look in the BIOS and disable secureboot if its on, fastboot, Intel Smart Response Technology (SRT) and FastStartup if you can see anything like that.

Now try booting from the USB again. If it is all working, ONLY use 'Something Else' when you get to the partitioning section of the install.

---

### Post by validust on 2014-01-05
"This computer currently has no  detected operating systems. What would you like to do?" - Aren´t there a number of options following that question? Three or four, one of which is "Something else".
   Oh... Bowing to Bucky Ball, and exiting.

---

### Post by Bucky Ball on 2014-01-05
> **validust said:**
> "This computer currently has no  detected operating systems. What would you like to do?" - Aren´t there a number of options following that question?

Think it doesn't detect the operating system because of EFI issue. I could be wrong. Win is installed so it should be detecting an operating system, but known not to if not booted in EFI mode.

If you go ahead from here, with Ubuntu not detecting the installed OS, it has the potential to wipe the OS as Ubuntu uses the whole drive to install. ;)

---

