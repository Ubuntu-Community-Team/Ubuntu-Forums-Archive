---
title: "totally messed up laptop"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by drcomic on 2008-01-10
I have a laptop that is totally messed up and I need some help.
I am not afraid to tinker and have tried to solve the problem, myself, but to no avail.

Here is what I have done so far...
1. I have a Toshiba laptop satellite, pentium III
2. I installed Ubuntu (one version just before 7.1) & everything worked fine.

Well i decided to update thru the online method inside the desktop software (my mistake i know, didn't read that the manual update from disk was better)

computer got thru to the clearing and restarting and then hung on the reboot.

I downloaded 7.1 to a cd and burned the iso.  I can boot to the start up cd.

I tried to solve the problem with (?)
linux repair or repair linux (can't remember which) didn't work.

so then in all of my wisdom, i thought i could just wipe it out and start again, so...

I downloaded and used Gparted to destroy the partion and redo it.  (i may need to post on gparted forum ?)  I have deleted and reset the partion.  No luck.

I have even tried the Super Grub disk.  No luck.  I have obviously messed up the grub as well.

Here is what the laptop screen shows when it get stuck trying to reinstall any system...

VFS: Cannot open root device "<NULL>" or unknown-block (104,1)

Please append a correct "root=" boot option:
here are the available partitions:

Kernel panic - not syncing: VFS: unable to mount root FS on unknown-block (104,1)

thanks for any help anyone can provide.  I want to get back to installing Ubuntu on this laptop.

---

### Post by dstew on 2008-01-10
Do you get those error messages when you try to boot the LiveCD, or during the installation process? Can you run the LiveCD Ubuntu system?

---

### Post by billgoldberg on 2008-01-10
I don't see why formatting the hard drive using gparted live cd and then installing ubuntu 7.10 wouldn't work.

I hope you made back-ups.

---

### Post by drcomic on 2008-01-10
answer to first post.  Yes.  It did it when i try to reinstall.

2nd post.
Question:
I have the disk label type as msdos
partition: /dev/hda1
filesystem: ext3 (I changed this a couple of times so let me know what i need)

Information shows the following:
status: not mounted


What should i do to reformat and what file system.  (i am new to linux, as if you can't tell)

thanks for the quick replies!

---

### Post by drcomic on 2008-01-10
> **dstew said:**
> Do you get those error messages when you try to boot the LiveCD, or during the installation process? Can you run the LiveCD Ubuntu system?

I can boot the live cd and get the menu.  This is where I tried the F6 and used the text commands to attempt the "Linux repair"

I get the error message during the installation process and during the repair process.

The Ubuntu cd boots up just fine.

thanks for the quick reply and any help.

---

### Post by Golem XIV on 2008-01-10
2 things:

1. Do you have any files/documents/music saved on your laptop's disk that you want to keep?  You have already hosed the partition, so in this case I would recommend to do NOTHING and get some additional help on how to recover damaged partitions.  I did it once, but I was careful to not write anything else on that disk after I accidentally killed the partition.

2. In case you have no files worth keeping and you don't mind wiping the entire disk, just boot off the Live CD and install from scratch with the installer.  If you don't want to mess with partitioning, select the "Use entire disk" partitioning option.

---

### Post by drcomic on 2008-01-10
> **Golem XIV said:**
> 2 things:

1. Do you have any files/documents/music saved on your laptop's disk that you want to keep?  You have already hosed the partition, so in this case I would recommend to do NOTHING and get some additional help on how to recover damaged partitions.  I did it once, but I was careful to not write anything else on that disk after I accidentally killed the partition.

2. In case you have no files worth keeping and you don't mind wiping the entire disk, just boot off the Live CD and install from scratch with the installer.  If you don't want to mess with partitioning, select the "Use entire disk" partitioning option.

This is the problem.  When I try and run the installer from the Ubuntu CD i get the message in my first post.  The computer just stops with that on the screen.

I do not have anything on it i want to keep.  I just want to be able to install Ubuntu again.  I can not get it to do anything because I keep running into that problem (see my first post).

I think i have somehow messed up the partition in such a way that it will not allow the full install.

I can view my hard drive with gparted, but not sure which file system to set up?

---

### Post by dstew on 2008-01-10
OK, I want to know if you can get the Ubuntu LiveCD *system* up and running, where you have the desktop with the icons on it. It seems from your post that you get the initial LiveCD menu only, then you get the errors when you select the Start or Install Ubuntu menu item. Am I correct? If so, your problem is with the LiveCD interacting with your hardware, possibly with your video card. You can try F6 boot options such as **quiet nosplash** or **noapic nolapic**. [Here]("http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php") is an exhaustive list. This is assuming the disk is good. Did you check the hash value on the downloaded iso file? Try the Check CD for Defects menu item. Finally, you can use the Alternate Install CD to try to re-install or repair your system. It is a text-based installation disk that installs the same Ubuntu system, but uses less hardware resources than the LiveCD. You get it from the same Ubuntu download page (check the box below the Start Download button).

---

### Post by mc4man on 2008-01-10
try going back to gparted and deleting all partitions, just 1 big unallocated space. Then try installing from live cd. With an old system like yours you may need to use the alternate install cd instead. How much ram do you have?

sorry already answered

---

### Post by drcomic on 2008-01-10
> **dstew said:**
> OK, I want to know if you can get the Ubuntu LiveCD *system* up and running, where you have the desktop with the icons on it. It seems from your post that you get the initial LiveCD menu only, then you get the errors when you select the Start or Install Ubuntu menu item. Am I correct? If so, your problem is with the LiveCD interacting with your hardware, possibly with your video card. You can try F6 boot options such as **quiet nosplash** or **noapic nolapic**. [Here]("http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php") is an exhaustive list. This is assuming the disk is good. Did you check the hash value on the downloaded iso file? Try the Check CD for Defects menu item. Finally, you can use the Alternate Install CD to try to re-install or repair your system. It is a text-based installation disk that installs the same Ubuntu system, but uses less hardware resources than the LiveCD. You get it from the same Ubuntu download page (check the box below the Start Download button).

I can not get the LIVECD up and running. When I choose the option to install i get the message from my first post.
I have tried creating just a large unpartitioned drive.  Still getting the same message.
I have tried with both options and getting the same message.

I did not have this problem until I did the upgrade and then messed with the system.

I am still getting...

VFS: Cannot open root device "<NULL>" or unknown-block (104,1)

Please append a correct "root=" boot option:
here are the available partitions:

Kernel panic - not syncing: VFS: unable to mount root FS on unknown-block (104,1)

What is block (104,1)?  This seems to be the hanging point.

I used to be able to run the older version of Ubuntu with no problems.

---

### Post by dstew on 2008-01-10
The problem is not with your disks or your paritions, but with the LiveCD interacting with your system. Did that particular LiveCD work in your computer before? How about the older 7.04 live CD?

---

### Post by zabien1970 on 2008-01-10
Do you still have your old live cd, probably 7.04, if so see if you can run that

---

