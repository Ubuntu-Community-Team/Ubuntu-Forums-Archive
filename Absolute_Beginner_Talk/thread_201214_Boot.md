---
title: "Boot"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by J0E0NE on 2006-06-21
Well I've been using linux for a few months now and its gr8 so i formatted my Hard drive and put linux on it alown, used it for a few days and missed a couple of games so i bought another hard drive.
Ive just put windows on the new hard drive and when i start up i cant choose which hard drive to boot from, it just auto boots from the windows hard drive.
What am I doing Wrong?

---

### Post by tokyo on 2006-06-21
[QUOTE=J0E0NE]Well I've been using linux for a few months now and its gr8 so i formatted my Hard drive and put linux on it alown, used it for a few days and missed a couple of games so i bought another hard drive.
Ive just put windows on the new hard drive and when i start up i cant choose which hard drive to boot from, it just auto boots from the windows hard drive.
What am I doing Wrong?[/QUOTE]

did you configure the GRUB bootloader for your new harddrive?

im not sure on the specifics of it, but im sure it can be done.

---

### Post by rowanparker on 2006-06-21
When you install Windows it installs its bootloader to the hard drive.
You need to use the CD to reinstall Grub.

Rowan.

---

### Post by J0E0NE on 2006-06-22
Errr im a complete newb could someone explain step for step how to do this please?

---

### Post by Herman on 2006-06-22
Okay, the first sector of your (first) hard disk is where your BIOS looks for instructions when it is booting up your computer. It has a special name, it is called the 'Master Boot Record', or 'MBR' for short. The MBR contians an 'IPL' or 'first stage' of a bootloader, and the partition table.
Basically, for our purposes, it is good enough to say that the 'IPL' for the bootloader is a lot like a sign on a highway that points the BIOS in the right direction to whatever partition contians the files that make the bootloader work.

So if Ubuntu has a bootloader 'installed to MBR', it just means it has a sign in the MBR pointing to Ubuntu, where GRUB's files are. Then GRUB gives your the GRUB menu and lets you choose which operating system you want to boot.
 When Windows was installed on your hard drive, it turned the sign around and made your MBR point to Windows and will only boot Windows (unless you configure boot.ini, but that's far too complicated for most people).

To fix that and make your MBR point to Ubuntu again, you need to 're-install GRUB'. As GRUB re-installs, it should automatically see that there is another operating system there on your disk (Windows) and it will automatically include it in your new GRUB boot menu. 
To install GRUB to MBR, 
EDIT:  Here are some links with lots of good ways to re-install GRUB:
 [Re-installing GRUB ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29")   |     [  Swiss2K thread]("http://www.ubuntuforums.org/showthread.php?t=114332")    |     [Arnieboy thread]("http://ubuntuforums.org/showthread.php?t=76652")   [vnbuddy2002 thread]("http://www.ubuntuforums.org/showthread.php?t=24113")
Regards, Herman.

---

### Post by J0E0NE on 2006-06-23
Ok thanks

---

