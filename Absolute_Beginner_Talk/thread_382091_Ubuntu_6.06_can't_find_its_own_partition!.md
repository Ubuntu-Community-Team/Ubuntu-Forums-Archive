---
title: "Ubuntu 6.06 can't find its own partition?!?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by marcelvanwijk on 2007-03-11
Okay, I finally decided to bite the bullet and try Linux, mostly as a web development environment with Apache, PHP & MySQL, next to my copy of WinXP. My machine has P3-650MHz, 128Mb, and a 80GB IDE HDD.

So I've downloaded the alternate distro version 6.06 LTS for i386, burned the .iso to CD. I've set up partitions (a 10GB boot partition and a ~0.75GB swap), allowed grub to boot from the MBR, and installation went without a hitch. Then the system reboots and BLAM! I get the following message:

ALERT! /dev/hde3 does not exist!

and it crashes to the shell prompt.

My partition table looks like this (approximate numbers). Everything resides on a single HDD.
44GB NTFS
20GB FAT32
10.7GB ext3
0.75GB linux swap

(What's also strange.. I explicitely set up the Linux partition to be ext3, but during bootup it indicates it's ext2.)

I also tried deleting the partitions I made and let the Ubuntu installer figure it all out by just selecting "use largest continuous space", with the same results.

Anyone out there feeling like helping a Linux-newbie? :)

---

### Post by astrolabio on 2007-03-11
you sure is /dev/hde3 and not /dev/hda3?

---

### Post by marcelvanwijk on 2007-03-11
/dev/hde3, that's what is says...

---

