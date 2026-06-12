---
title: "Boot up screen"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by merlined on 2006-02-25
I was just wondering if this boot up screen (the "grub" screen) was suppost to have so many options, and if so what are they for.

My grub screen has this:

Ubuntu Kernel 2.6. 12-10-388
Ubuntu Kernel 2.6. 12-10-388 (recovery)

Ubuntu Kernel 2.6. 12-9-388
Ubuntu Kernel 2.6. 12-9-388 (recovery)

Ubuntu, mentest86+

Other operating systems

Ubuntu Kernel 2.6. 12-9-388 (on/dev/hda2)
Ubuntu Kernel 2.6. 12-9-388 (on/dev/hda2) (recovery)

Ubuntu, mentest86+ (on/dev/hda2)

Microsoft Windows xp
Microsoft Windows xp


It seems like something is not right here. I just want Ubuntu and windows.

Also, I was wondering how to access my files that are located in the "my documents" in windows. And also, I have a second hard drive I would like to access because it has a lot of stuff on it and it is a fat32 format. But I have not been able to figure out how to get to my files.

Thank you in advance!

---

### Post by BeatBoxRocker on 2006-02-25
Grub has so many options to select because you have upgraded the kernel and it keeps the old kernel startup. It seems that you have tried to install (K)ubuntu several times or you have two ubuntus in different partitions in your hard disk.

It isnt a problem because if you select the first option "Ubuntu Kernel 2.6.12-10-386" and one of the "Microsoft WinXP" it should boot with the desired operating system. You could clean up the options that GRUB shows deleting some entries in the file /boot/grub/menu.lst Take a look at it.

To access the files in another partition you have to edit de fstab file in the folder /etc. It allows you to mount any partition in the system with the permissions you want (for example read only).  This is the line you should add to read files from hda1 that is the drive where WindowsXP is in my Hard Drive. Maybe You will have to modify hda1 for your box.

/dev/hda1       /media/hda1     vfat    defaults        0       0

Saludos!

---

### Post by Sandlst on 2006-02-25
I found this guide very helpful for mounting my fat drive (stolen from aysiu's sig) check it out [http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

---

