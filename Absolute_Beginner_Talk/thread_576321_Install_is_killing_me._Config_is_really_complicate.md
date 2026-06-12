---
title: "Install is killing me. Config is really complicated. Help."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Asharale on 2007-10-15
I recently installed Ubunto on my machine. I have an Asus motherboard (A7N8X-E) with Nvidia, twin 200GB sata, and I want to run Ubuntu on both hard drives. I took Windows XP off last week and I am still trying to get the system to boot. I started with error 21, then I got to error 17, I have looked at all of the posts involving: dual boot, raid, mdadm, error 21, error 17, supergrub, and every other install guide I could find, and I have really screwed this machine up. I think I have deleted raid because i cant find either of my hard drives in the bios. On startup I can get up to "press F4 to get to Raid utilities" and no further. I then have to startup with the live disk.

I dont need my computer to read both disks as one, I am fine with 2 seperate drives. I dont thing this motherboard will allow that and I dont care. 1 drive is fine too. I dont want Windows. I have downloaded Mdadm but I dont know how to configure it. I cant even access it. I can see it. I just cant get it to do anything. 

I need to know how to get this thing to start up. I am at square 1....Again.


I am determined to make this work. I am just in way over my head right now.

---

### Post by bvmou on 2007-10-15
Maybe unplug one drive for the moment, you will be able to install Ubuntu with GRUB on the MBR of that drive even if the motherboard identifies it as secondary.  You can boot from there, then add the other volume to fstab and do backups with rsync or another tool.  Are you working with the 7.10 beta or 7.04 -- my suggestion would be to start with the former.  I had an unusual problem along these lines the first time I installed on a new motherboard with EFI.

---

### Post by caedmon on 2007-10-15
Hi!
 The Grub errors look as though things are getting confused at boot up. 
How did you install, through the CD? If so If you are able to run from the live cd you can run gparted to see whats happening on your hard drive.

I had the same problems recently but got there after several attempts, somehow my drive wasn't formatting properly, hope this helps until someone comes along.

:lolflag:

---

### Post by djchandler on 2007-10-15
> **Asharale said:**
> I recently installed Ubunto on my machine. I have an Asus motherboard (A7N8X-E) with Nvidia, twin 200GB sata, and I want to run Ubuntu on both hard drives. I took Windows XP off last week and I am still trying to get the system to boot. I started with error 21, then I got to error 17, I have looked at all of the posts involving: dual boot, raid, mdadm, error 21, error 17, supergrub, and every other install guide I could find, and I have really screwed this machine up. I think I have deleted raid because i cant find either of my hard drives in the bios. On startup I can get up to "press F4 to get to Raid utilities" and no further. I then have to startup with the live disk.

I dont need my computer to read both disks as one, I am fine with 2 seperate drives. I dont thing this motherboard will allow that and I dont care. 1 drive is fine too. I dont want Windows. I have downloaded Mdadm but I dont know how to configure it. I cant even access it. I can see it. I just cant get it to do anything. 

I need to know how to get this thing to start up. I am at square 1....Again.


I am determined to make this work. I am just in way over my head right now.

Do you have the motherboard manual? Get it at [http://www.asus.com.tw/support/cpusupport/cpusupport.aspx](http://www.asus.com.tw/support/cpusupport/cpusupport.aspx)
My guess is you need to delete the old RAID configuration first, then create a new one. See section 5.5.2 of the manual to do this. Then try installing Ubuntu.

DJ

---

### Post by giannisfs on 2007-10-15
I think you need to see First this-->```
http://ubuntuforums.org/showthread.php?t=408461
```
and  second Consider reinstalingl your linux distro as a solution -and this time be more carefull...

You might find extremely useful to  learn to search with keywords and learn to filter the results 
Learn the basic commands and their arguments in the linux console (usually debian for ubuntu)

I am sorry i am not yet capable for answering you the ultimate easy and robust solution 
BUT i am sure that is better for you to reinstall it , cause you are not always need to know a "why"
but you are always need to know a "how".Iit sounds the same but is not because computers are  machines and machines are not living creatures so they can't take care of them selfs.But machines are being controlled by the software the OS and the drivers.SO evn if you will never build a hard disk you can easilly understand the how it was made.SO software and operating systems can't  harm a hard drive
they can configure it just because of the driver which is made to make it work not to destroy.
As soon as you have a hard drive it means that your system does not see a "driver" and that leads to make you find the how to put that "driver" working... and so on see these links 
```
http://www.drivermuseum.com/files/utils/hd_u.html  
```
```
http://support.wdc.com/
```:guitar:
***_NEW EDIT SEE BELOW_***
Also see the above post from  bvmou  which i think is what  you should do _except_  if you try a usb linux like dsl(damn small linux) or knoppix or other to solve your problem faster.   Those distros come along with software that managing hard drives Also you may skip the reinstalling of an Operating system  until you solve the problem

---

### Post by Asharale on 2007-10-15
Sorry I took so long to reply, I unplugged one of the drives and reinstalled. I tried to boot from the hard drive and got the same ctrl-s screen. since then I cant even get the live disk to load. I reset the bios to the defaults and it would let me boot from a DSL disk but would not let me use my ubuntu live disk. I was just now able to check the thread (from my Treo) and it will be a few hours before I can attend to the machine again. I have my manual for the motherboard and will let you know what happens after I delete raid.

---

### Post by djchandler on 2007-10-21
> **Asharale said:**
> Sorry I took so long to reply, I unplugged one of the drives and reinstalled. I tried to boot from the hard drive and got the same ctrl-s screen. since then I cant even get the live disk to load. I reset the bios to the defaults and it would let me boot from a DSL disk but would not let me use my ubuntu live disk. I was just now able to check the thread (from my Treo) and it will be a few hours before I can attend to the machine again. I have my manual for the motherboard and will let you know what happens after I delete raid.


Did you check the Live CD for errors before installing? If you did, this could be a hardware failure problem, either your IDE interface on the motherboard, or maybe the CD/DVD drive you are trying to boot from. Have you disabled the IDE interface not in use? See if your Live CD will boot on another computer or different CD drive if you can substitute a different one in your computer. 

Good luck!

DJ

---

### Post by Flying caveman on 2007-10-22
I don't even pretend to understand patitions, let alone different raid configurations, I try to keep it simple by using one disk,  and even still I occasionally mess something up.  SuperGrub disk is the way to go!

---

### Post by Asharale on 2007-11-02
Okay,
First of all thanks for responding to my post, I appreciate all of the help. 

So far I have been able to get the machine back to where it will boot from the live disk again. 

This is what I have tried so far. 

1. Install Ubuntu 6.10 in place of Windows XP. No other OS installed. Raid 0. (the beginning of my grub errors) I got error 21.

2. Install again with 1 drive unplugged. I got both error 17 and 21. 

3. Set raid to 1 and installed again. I restarted and got conflicts in the raid array and rebuilt the mirrord set. Then got error 18. ASUS forum suggested adding noacpi to the end of the boot line, but I hit F6 and add it, and then what? Its not there when I restart.

2. I am working from a live disk, so some of the things I've tried, have no effect after I reboot.

Has anyone had any luck with linux and this motherboard?

---

### Post by jaybombalous on 2007-11-02
I thought error 17 meant the CD was corrupt and u needed to re-d/l the CD image.

Did u check the CD before u installed ubuntu with it? There is an option when u boot to the cd, it says verify the CD image.

---

### Post by Asharale on 2007-11-02
I verified the CD image and it's good. I can't install any linux OS. I tried DSL and got the same errors.

---

