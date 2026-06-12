---
title: "ubuntu multiple issues"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Sham885 on 2008-04-10
My computer was having various system errors that eventually led to xp giving me a blue screen and refusing to load anything.  I put my harddrive in an external case, connected it to this computer, and backed everything up planning to do a clean windows install.  Since I've been considering installing linux for awhile I decided I might as well do that too.  I partitioned the drive for 175gb to use windows, 50gb to install ubuntu, and that left ~20gb unpartitioned.  Burnt the live cd, set the bios to boot cd followed by usb device, and installed ubuntu on the 50gb partition using the leftover space for swap.

Biggest problem is now I can't start this computer if I unplug the external.  It says GRUB loading stage 1.5 followed by error 21.  If I plug in the external I can load windows fine.  I really need to fix that before I put the harddrive back into my computer.

Problem 2 loading ubuntu leads to the error message "Cannot Display this Video Mode" and I can't do anything but turn off the power and start again.

---

### Post by bobplano on 2008-04-10
For your first problem, the best solution I can think of is reinstalling GRUB (how to do so [here]("http://ubuntuforums.org/showthread.php?t=224351")) and set the boot order in your BIOS so it boots from the usb drive as first priority. 

for the second issue, use your live cd again to change the drivers, in your /etc/X11/xorg.conf, to "vesa". If that doesn't work, please post your graphics card and moniter so someone smarter than me can come along and help

---

### Post by alphaniner on 2008-04-10
The reason problem #1 is occurring is because GRUB, which is installed onto the MBR of your internal drive, is looking for a folder on your USB drive (/boot/grub on your Ubuntu partition) to tell it where the OSs are.  bobplano's solution should work, but you will probably have to do some reworking *again* after you put the drive inside the PC.  If I were you, I would just put the drive in the box and reinstall Ubuntu.  Don't get me wrong, your install could be saved, but this is probably the least painful solution.  The alternative, I believe, would be to manually edit /boot/grub/menu.lst.

For problem #2, try booting into recovery mode and do the following:

1) make a backup of your current xorg.conf file

```
cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

Yeah, i know its already completely borked, but its always a good idea to make a backup.

2) run the command

```
dpkg-reconfigure xserver-xorg
```

and after that is done, try booting normally again.

---

### Post by Sham885 on 2008-04-11
I don't want to install anything on the internal drives.  It's my mom's office computer.  I want xp to load normally.  It would be nice to be able to load ubuntu from an external when using other computers but not if it messes with the standard windows boot.  I tried loading the xp recovery cd to fix it but it asks for which windows install I want to load.  I have no idea what it means since there is only 1 install and I tried every option without getting anywhere.  How do I just fix the MBR to load xp?

Ubuntu is loading fine now from both the external and in my case.  Currently it's the only os I have on my computer since xp won't install until I get the drivers for my sata hd.

---

