---
title: "shared files between xp and linux"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by afflusso on 2006-08-30
This is really a hypothetical question because I'm not having any problems... yet. But if I were to dual-boot ubuntu and windows xp on the same hard drive, would I be able to access any files from both os's without duplicating them? 

For example, if I have a 2GB movie, I don't want to have one copy for XP and one for ubuntu, so would I be able to access the file from both operating systems?

---

### Post by madmetal on 2006-08-30
the most reliable and easy way to do so is to create a fat32 partition where you can place all your files and documents to have access from both ubuntu and windows...

---

### Post by afflusso on 2006-08-30
> **madmetal said:**
> the most reliable and easy way to do so is to create a fat32 partition where you can place all your files and documents to have access from both ubuntu and windows...

So without creating the FAT partitiion, I couldn't access files in Windows from ubuntu?

---

### Post by AntiFlash on 2006-08-30
ditto above.  there have been many attempts for linux to gain read/write access to NTFS partitions, but none that have been blessed on any large scale...it is not the best FS to use which is why I personally went with an EXT3 partition for my data.  that forced me to stick with linux for the majority of what I do on the computer...which is good.  The fat32 should get you by until you decide to cutover to Linux full-time :D

---

### Post by madmetal on 2006-08-30
you can find more ways to do so but i think this is the most easy and reliable...

---

### Post by halitech on 2006-08-30
going from ubuntu to xp shouldn't be a problem reading but if your main drive is ntfs, it can cause problems writing to the xp partition. I honestly dont know about reading the ubuntu partition from xp.

---

### Post by AntiFlash on 2006-08-30
you will have read only access in linux of you windows data.  windows cannot/will not read linux partitions at all...

---

### Post by VirtuAlex on 2006-08-30
You'll have read only access to your windows partition by default - good enough for movies. You can install driver to access ubuntu partition from windows with full read-write access. But best way to share both ways in read/write mode is to make separate fat32, as madmetal suggested.

---

### Post by Omnios on 2006-08-30
Linux can mount and read ntfs but to write to it is a problem as there is a chance of corruption so it is not used you can copy a software package from ntfs to linux though. Also there is a program that can read ext2 and 3 and if I remember correctly it can read and write. 

 My personal set up is to have my XP partition, A linux test partition which has Fedora core 5 on it. A seperate hard drive with Ubuntu and grub and a seperate documents set with vfat to shate as a windows My Documents drive and a Ubuntu documents drive. This allows you to save most of your data if there is a problem with your windows or linux partitions. 

 There are many options and you could possibly make a documents drive formated as either vfat or Ext2.

---

### Post by afflusso on 2006-08-30
So I can read XP files from ubuntu, but not vice-versa. Sounds good enough. When/if I decide to convert, when/if I have any problems, I'll know where to go for some help. Thanks.

---

### Post by VirtuAlex on 2006-08-30
by default yes, but there are drivers for windows to read linux partitions, for example this one:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by wana10 on 2006-08-31
how i have mine set up is windows as ntfs (linuc cannot read) and then my / and my /home partitions are ext3, which with the driver in the post above mine windows can read. so my /home drive is my shared area twixt the two

---

### Post by Frank Golden on 2006-08-31
> **afflusso said:**
> So I can read XP files from ubuntu, but not vice-versa. Sounds good enough. When/if I decide to convert, when/if I have any problems, I'll know where to go for some help. Thanks.
That is true you have read priveleges to your XP partition.
You will need to mount the XP partition to read from Ubuntu.
The following Tutorial has info on how to auto mount
so your XP install and all it's files are available (read only) from Ubuntu. There are experimental methods of writing NTFS
from Ubuntu but they are too risky for casual use. Besides what better way to protect your XP install and included data than to have it read only?

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

Read through the table of contents of the above for info on automounting.

I have a dual boot XP pro + Ubuntu 6.06.1 LTS on my laptops 120GB
HDD. The first three partitions are NTFS (XP, pagefile and XP data etc.) I have a fairly large Fat32 shared partition, where I
store stuff common to both OS's including a partimage backup
of my Ubuntu install. Ubuntu is on the last 19.0GB of drive.
I have MP3 files stored in my NTFS data partition because it is the largest partition, I can play them perfectly from both operating systems.
My NTFS stuff is safe from inadvertant corruption by being read only.
I can read/write Ubuntu from XP by installing

[http://www.fs-driver.org/](http://www.fs-driver.org/)

When you install on your XP machine it places a control in you
Control Panel. When you click on it it shows your ext3, ext2
partitions (Ubuntu) and let's you assign drive letters to them.
They can now be seen in My Computer. You can change stuff here
that Ubuntu would normally not let you do, so be careful.
What I do is leave no drive letters for my ext3, ext2 partitions
unless I have a good reason to go there from XP. Then I tread lightly.
Never change system stuff and be careful with editing other stuff
as XP can messup permissions in Ubuntu. You are better off making changes to Ubuntu from Ubuntu using the normal procedures.

I only use when I want to export data to my /home in Ubuntu.

---

### Post by VirtuAlex on 2006-08-31
> **wana10 said:**
> how i have mine set up is windows as ntfs (linuc cannot read) and then my / and my /home partitions are ext3, which with the driver in the post above mine windows can read. so my /home drive is my shared area twixt the two
This driver is not perfect too. For example it will screw up filenames from different code pages.

---

### Post by BiggoCharley on 2006-09-01
The program found here will create a windows drive letter for your ext2 home (or other) folder. I use this and it works very well-- very simple to use and its freeware.<www.fs-driver.org>

---

