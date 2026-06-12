---
title: "Installing Ubuntu on a Vista machine - problematic?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ubuntukid on 2007-03-20
I've got a windows vista machine which I wish to run ubuntu on as well. Now I've heard that Vista uses a modified version of NTFS and I should therefore not use linux partitioning tools. Well luckily windows vista now includes it's own partitioning tool, so I've resized my vista partition so that I now have an empty 10 gb FAT32 partition for installing ubuntu on.

I just want to make sure that there isn't anything I need to know before I actually install ubuntu. Does GRUB identify Vista and setup dualboot properly? Is there anything else I should know about before installing ubuntu?

Also, I would like to try the test version of ubuntu 7.04. Could it potentially damage my vista partition seing as it's still in alpha stages? I don't mind reinstalling ubuntu because something went wrong, but I don't want to do the same with windows, because that would take half a day.

---

### Post by dreamsayer on 2007-03-20
> **ubuntukid said:**
> I've got a windows vista machine which I wish to run ubuntu on as well. Now I've heard that Vista uses a modified version of NTFS and I should therefore not use linux partitioning tools. Well luckily windows vista now includes it's own partitioning tool, so I've resized my vista partition so that I now have an empty 10 gb FAT32 partition for installing ubuntu on.

I just want to make sure that there isn't anything I need to know before I actually install ubuntu. Does GRUB identify Vista and setup dualboot properly? Is there anything else I should know about before installing ubuntu?

Also, I would like to try the test version of ubuntu 7.04. Could it potentially damage my vista partition seing as it's still in alpha stages? I don't mind reinstalling ubuntu because something went wrong, but I don't want to do the same with windows, because that would take half a day.

Personally, I wouldn't install 7.04, you should install 6.10. It's stable and being a new user until you become familiar with Ubuntu.  

GRUB should find Vista no problem, but I would delete the fat32 partition first from within windows and leave it as free space. During Ubuntu install select "use free space". The partitions will automatically get setup for you.

---

### Post by wxnker on 2007-03-20
If you have problems you can try looking at this tool for Windows Vista:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

It is a program that will help you setup a bootmanager that can start Ubuntu ... and even Vista if you want hehe.

When I was using Vista I just installed Ubuntu and chose to install "GRUB" on the Ubuntu partition and NOT the MBR (Default). This can normally be changed right after the "partition setup" during the install of Ubuntu by choosing the button "ADVANCED" just before the installation starts copying files.

Default is MBR (0) but you can choose to install GRUB (Linux boot menu) on the Ubuntu partition instead. All you need to know is which partition Ubuntu is being installed on, hda1, hda2 or hda3 etc.

When choosing where to put GRUB the numbers are different, like this:
0,0 = hda1
0,1= hda2

etc...

After the installation you can boot into Vista, install the tool from neosmart (EasyBSD) and setup the boot options from a graphical GUI.
I fond using EasyBSD easy because back then I had no idea about GRUB and Linuxboot. Setting it up with that tool in Vista is real easy.

---

### Post by testube_babies on 2007-03-20
I'm currently dual-booting 7.04 with Vista, no problems.  However, I partitioned my hard drive BEFORE installing Vista.  Otherwise, the default Grub options work fine, and even recognize that I'm running Vista instead of XP.

---

