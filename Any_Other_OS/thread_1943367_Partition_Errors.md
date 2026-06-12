---
title: "Partition Errors"
date: 2012-03-18
forum: Any Other OS
---

### Post by kelvinho on 2012-03-18
Hi there SRS. I tried your program in Debian, and I didn't succeed in fixing my own particular problem. I am mightily upset, as I went to great lengths to copy all my files to another partition, and now there is a blank space where they should be - across two separate partitions.

Through a program in Windows called Acronis, I can see that both partitions are where they should be. I can even examine the files. 

But when I boot into Linux, both partitions, which are at the beginning of the logical volume, simply disappear. Before this happened, I had a similar fault that I have read about somewhere else in a similar thread ... that a particular partition appears twice in Diskmounter. 

After noticing this, I rebooted and lost grub, and I had to use Gentoo Live to mount my boot partition to put grub back into place. I distinctly remember being able to mount one of the lost partitions then, but after rebooting, I have had no success finding the partitions in Debian. Gparted shows a blank partition map, and disk utility shows a shrunken logical volume.

The error from my terminal with fixparts is as follows.

root@debian:/home/kelvin# fixparts /dev/sda
FixParts 0.8.0

Loading MBR data from /dev/sda
Unable to seek to 4623007744! Aborting!
MBR signature in logical partition invalid; read 0xE3C1, but should be 0xAA55
Segmentation fault

Many thanks in advance to whoever should come to my aid!

---

### Post by oldfred on 2012-03-19
You were in this old Solved thread:
[http://ubuntuforums.org/showthread.php?t=1744799](http://ubuntuforums.org/showthread.php?t=1744799)

But it does not seem that your issues are the same. Fixparts normally solves partition table issues, but not necessarily overlapping partition tables. Original thread also mentions gpt, do you have gpt partitions?

Do you have Ubuntu liveCD? I an not sure of the differences of Debian.

From Ubuntu post these:

sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
#if gpt the fdisk above will not really work but then run this. gdisk is in Ubuntu repositories or you can down load from same site you downloaded fixparts.
sudo gdisk -l /dev/sda

Reference on previous thread to fixparts:
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

