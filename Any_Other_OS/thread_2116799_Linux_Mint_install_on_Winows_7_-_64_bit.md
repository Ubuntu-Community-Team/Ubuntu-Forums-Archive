---
title: "Linux Mint install on Winows 7 - 64 bit"
date: 2013-02-16
forum: Any Other OS
---

### Post by a.v.l on 2013-02-16
Having been a Ubuntu user for a while, I switched to Mint 13  recently. All was well until I had to buy a new PC which had Windows 7 - 64bit installed. 

It hasn't taken me long to realise how much I dislike it. So I thought I would dual boot using Mint 14 along side Windows 7.  I used the Mint 14- 64 bit iso disc and got as far as the Linux Mint desktop. Everything worked great from the CD. From there I clicked on the install Mint icon on the desktop to start the dual boot install. When the install process came to choosing how much windows 7 and Mint should share of the Hard drive, I slid the slider to share the partition between windows and mint, slightly giving Windows 7 more space to store images. A moment later a warning box appeared from the Mint installation, which said that Mint could not be installed and to check the CD was clean. Now here is my problem.

Before the dual boot installation attempt, I had a 2 Terabite hard drive, now its showing that my hard drive size is down to 1.3 Terabites. Where did the .7 TB go to and how do I get it back? This computer is still under guarantee so before I mess things up any further, can someone advise please.

---

### Post by howefield on 2013-02-16
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by montag dp on 2013-02-16
It sounds like the installer resized the Windows partition before quitting.  It shouldn't really be a problem.  If you want to recover it in Windows, you should be able to do it using the disk partitioning tool that comes with Windows (always make sure you back up everything first before you do any partitioning operations on the hard drive!).  Or, if you still want to install Linux Mint, just select the 0.7 TB portion of the drive for the install.

For what it's worth, I dual boot Mint 14 and Windows 7 on my laptop.  Attached is a screenshot of my partitions from the KDE partition manager. sda2 is the Windows partition, and I created a logical partition within sda3 which is the Linux partition.  You can achieve this type of arrangement by using the "manually create partitions option" (or whatever it's called) in the installer.

---

### Post by a.v.l on 2013-02-17
> **montag dp said:**
> It sounds like the installer resized the Windows partition before quitting.  It shouldn't really be a problem.  If you want to recover it in Windows, you should be able to do it using the disk partitioning tool that comes with Windows (always make sure you back up everything first before you do any partitioning operations on the hard drive!).  Or, if you still want to install Linux Mint, just select the 0.7 TB portion of the drive for the install.

For what it's worth, I dual boot Mint 14 and Windows 7 on my laptop.  Attached is a screenshot of my partitions from the KDE partition manager. sda2 is the Windows partition, and I created a logical partition within sda3 which is the Linux partition.  You can achieve this type of arrangement by using the "manually create partitions option" (or whatever it's called) in the installer.


I used windows disc management and re-sized the hard drive, thank you.

---

