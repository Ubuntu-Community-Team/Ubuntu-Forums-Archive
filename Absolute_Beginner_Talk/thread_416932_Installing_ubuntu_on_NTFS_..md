---
title: "Installing ubuntu on NTFS ."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ubugoda on 2007-04-21
Hello every body.

I'm trying to install (ubuntu 7.04 amd6) on my gateway turion 64 x2 laptop.
i've already downloaded ubuntu and burned it .

the problem is that the hard disc is formated in only one NTFS partition and i've heard that ubuntu system cannot read NTFS file system by default.

i want to install ubuntu WITHOUT FORMATTING OR UNINSTALLING WINDOWS XP.what's your opinions??

Thnaks alot .

---

### Post by sonny on 2007-04-21
I think you should try rezising you NTFS partition, in order to do it, I recommend that you first defrag your partition with the system tools in Windows. After doing so, put in the live cd, and BEFORE installing use gparted (you can install it through synaptics, even if you are in live cd mode) to resize your partition and create a free space to install ubuntu. Then you can install as normal, when you are asked to choose the partition method just say manual (or custom, I don't recall the name of the option) and choose your free partition.

---

### Post by Sef on 2007-04-21
> i want to install ubuntu WITHOUT FORMATTING OR UNINSTALLING WINDOWS XP.what's your opinions??


Impossible to do.  You can't install an operating system without having the correct file system.  You can dual boot and have part of the partition ext 3, which Ubuntu can install on.

To dual boot from the Live CD, read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

To dual boot from the alternate cd, read the [Illustrated dual boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by BrewsterPilot on 2007-04-21
I can't emphasize one thing enough; DON'T use auto-partitioning. I learned that the hard way...

---

### Post by Hellcom on 2007-04-21
What you want is called dual booting. When you load the liveCD and chose to install you are given the option to resize your windows partition to make room for ubuntu. It will then use the free place to create a new partition in ext3 format along side of your NTFS partition (without effecting your windows install). When you boot up you are give an option between booting windows or ubuntu.

---

### Post by Corona on 2007-04-21
boot from the ubuntu CD and when you get to the desktop click on install. When you get to the part about partitions select manual and then you can re-size the partition from there and normally this works. When your done your windows system should be in tact and be available on the boot menu. I have done this many times with success but once it did fail. (probably my fault tho)

---

### Post by AusIV4 on 2007-04-21
> **BrewsterPilot said:**
> I can't emphasize one thing enough; DON'T use auto-partitioning. I learned that the hard way...

Really? I've had it work fine on several occasions. It's failed a couple of times, but it didn't cause any corruption.

---

