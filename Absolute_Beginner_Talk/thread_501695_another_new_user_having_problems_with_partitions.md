---
title: "another new user having problems with partitions"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by redtendoned on 2007-07-15
Hello everyone, seems like a great community I'm trying to slowly become a part of. I've been doing lots of reading on Ubuntu and have played around with the live cd for a couple days and I'm more than ready to make the switch. I was running through the 7.04 installation and got caught up at step 7 of 7. I would like to install Ubuntu on my 60 gb Hitachi internal harddrive as opposed to XP home edition. Here's the error I'm receiving, hopefully someone will be able to help me out, I'd really appreciate it.

How do you want to partition the disk
Guided - use entire disk
     SCSl1 (0,0,0) (sda) - 60.0 GB ATA Hitachi HTS54106
Manual

At this stage, I select the guided - use entire disk option and continue to step 5.

Installer comes up and tells me there are no users or operating systems suitable for importing from, which is plenty fine. Everything I wanted to backup from my Windows install is currently on my 80 gig Seagate external. Basically, I want to wipe this entire internal hard drive clean and start fresh with my brand new Ubuntu operating system, I go ahead and click forward to step 6 and fill out the "Who are you?" fields.

Ready to install:

If you continue , the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
SCSl1 (0,0,0) (sda)

The following partitions are going to be formatted:
  partition #1 of SCSl1 (0,0,0) (sda) as ext3
  partition #5 of SCSl1 (0,0,0) (sda) as swap

I click install and it makes it to 15% where it is "Detecting file systems" and an error pops up:
Failed to create a file system
The ext3 file system creating in partition #1 of SCSl1 (0,0,0) (sda) failed.

I feel like a jerk not asking for help already without even successfully being able to install, but I figured with a community of this magnitude that someone may have been there, done that and could point me in the right direction.

Any help would be wonderful, thanks much!

-Chris

---

### Post by Daveth on 2007-07-15
Is this feisty? I had problems with my SATA drive and the live feisty cd- it told me their was a fatal disk error. After running some checks, I used my dapper live cd to re-partition (with Gparted) without a problem. I'm not sure this gets you any further but it is my belief that SATA disks do still throw curved balls at Ubuntu and cause small problems.

How many times have you tried the install process?

---

### Post by annda on 2007-07-15
i highly recommend the [gparted liveCD]("http://gparted.sourceforge.net/livecd.php") for all partitioning woes.

---

### Post by ReaderRat on 2007-07-15
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by regomodo on 2007-07-15
i randomly get that error. sometimes it pops up, sometimes it doesn't

one time ubuntu install did this so i popped in the xubuntu disk. worked with xubuntu

---

### Post by Nitro2985 on 2007-07-15
I'm having pretty much the same problem, I tried booting up with the Gparted live cd, but I have an Nvidia graphics card and apparently it doesn't have the needed drivers to run on it, so I can't see what the hell it's writing on the screen.

Is there any other way besides Gparted to partition my disk in ext3?

---

