---
title: "Installing Ubuntu without removing OSX and XP Partitions?"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by pauliegnyc on 2008-05-12
Hi, I already have a dual boot of OSX and Windows XP. I'm wondering if it is possible to add a Linux partition to this without having to remove and reinstall the OSX and WinXP partitions.

Is this possible, or do I have to remove one (or both) operating systems to get Linux to be the third OS on my mac?

Thank you,

P

---

### Post by pytheas22 on 2008-05-12
I have only minimal experience using Ubuntu on a Mac, but I'm pretty sure that it shouldn't be any different than on any other computer.  You should be able simply to shrink the OS X and XP partitions and install Ubuntu in the freed space.  You could also try [wubi]("http://wubi-installer.org/") and not have to deal with partitioning (although for various reasons it's better to do a traditional install from CD if possible).  You might want to wait for confirmation from a Mac user that these options will definitely work before trying them, however.

---

### Post by cyberdork33 on 2008-05-12
> **pauliegnyc said:**
> Hi, I already have a dual boot of OSX and Windows XP. I'm wondering if it is possible to add a Linux partition to this without having to remove and reinstall the OSX and WinXP partitions.

Is this possible, or do I have to remove one (or both) operating systems to get Linux to be the third OS on my mac?You should be able to shrink one or both of the partitions with gparted, then install Ubuntu to the free space. Make sure you backup your information just in case!

There are often hiccups with Windows if you change the partitions after installing

---

