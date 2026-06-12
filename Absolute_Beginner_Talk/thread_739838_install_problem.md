---
title: "install problem"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by anim8tor on 2008-03-30
just picked up ubuntu today, got the program to run fine as a live cd. after I complete install and reboot, it gives me error 21. not sure what this means or how to fix it. i guess i should add that i'm installing on an old compac system as only os.

---

### Post by c-ron on 2008-03-30
It's a GRUB (GRand Unified Bootloader) error. What is the configuration of the harddrives in your system (check in your BIOS setup for master and slave drives for both primary and secondary IDE channels).

Also, when you made your linux partitions, where there any non linux partitions left on the drive? (Display the partition table of /dev/sda by booting with the LiveCD, open up a terminal and use fdisk -l /dev/sda )

These kind of errors are sometimes easy to fix, IF enough info is known about the system.
Usually a few edits to the /boot/grub/menu.list file can clear things up.

---

### Post by forestpixie on 2008-03-30
Can you boot to recovery mode - if you can once you've got to the command line run this, if you can't run in recovery mode - boot with the livecd and run it from there.

```
sudo fdisk -l
```

You're going to need the information that gives. When you start the pc - highlight the menu line for buntu and press 'e'

You'll get a line that says similar to this - we need to know the number you have 
> root hd(0,0)

---

### Post by anim8tor on 2008-03-30
Hey, here's the info you wanted as long as i copied it right, 

Disk /dev/hdb : 40.0gb, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
units= cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x0000675f


Device boot        Start       End            Blocks             id             system
/dev/hdb1              1        4777        38371221        83         Linux   
/dev/hdb2           4778     4867        722925              5         Extended
/dev/hdb5           4778     4867        722893+       82     Linux Swap/Solaris


think this is what you were looking for I'm running my disk drive as master and my hd as master/slave.

---

### Post by smurphy_it on 2008-03-30
Your information is quoting hard drive HDB.  This is the 2nd IDE hard drive.  Do you have another hard drive in this computer.  Perhpas running windows on it or something ?

---

### Post by forestpixie on 2008-03-30
and what do you get from the second bit of my post? - it should say

root hd(1,0)

---

### Post by anim8tor on 2008-03-30
there is only one hard drive in my comp, 

forestpixie i'm sorry but i dont really understand what i'm supposed to do for the second part when i turn the comp on it gives me the grub error right away, i guess the question is where do i go to press e sorry.

---

### Post by forestpixie on 2008-03-30
If you don't get the grub menu then you won't be able to do it - to get an e - you need to be at the grub menu. Might be best to reinstall grub, you can do it a few ways - you can use the livecd or an app called supergrub.

This page details the livecd way which is quite easy - also has bit on supergrub which I prefer.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by anim8tor on 2008-03-30
ok played around with it for awile and got this to return something

grub> root grub (hd0, <tab>

possible partitions are
partition num: 0, filesystem is ext2fs, partition type ox82
partition num: 4, file type unknown, partition type 0x82

so is my partition (hd0,0) ,and how do i install?

sorry again I'm not very good at code. and thank you for all your help.

---

### Post by forestpixie on 2008-03-30
Hi - not totally sure how you do it with the livecd I've always used supergrub. But you need to just use the info given at the "Quick Start" part of the help page.

No need to apologise - just copy and paste directly from the page the commands they give and you should be fine.

---

