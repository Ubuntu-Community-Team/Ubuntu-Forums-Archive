---
title: "Ubuntu, Win XP, Red Hat dual boot???????"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-27
I have a Windows XP machine and a running Ubuntu machine. On the windows machine the WinXP is installed on a 40GB drive as IDE 1 master and it has a second 5GB hard drive on IDE 1 slave that I use for backup images. While on the Ubuntu machine Ubuntu is installed on an 8GB hard drive on IDE 1 master and there is a 20GB hard drive as IDE 1 slave.

MY QUESTION IS:

On my Ubuntu machine I wish to make a dual boot Ubuntu with Red Hat Fedora, preferably leaving Ubuntu as it is on the 8GB hda and to have Red Hat on a 10GB partition on the 20GB hdb leaving 10GB of space both OS's can access.

On my XP machine I wish to make a dual boot Ubuntu with XP, preferably not touching the XP partition, installing Ubuntu on the 5GB hdb and leaving XP on the 40GB hda.

The Ubuntu machine is not that important in tearms of data stored on it, but I really really really want my XP machine to survive.

I have never done this before so any halp or tip will be apprechiated!

---

### Post by akiro.yamamoto on 2006-03-27
Well just back up the files from the 5GB hard drive, use the Ubuntu Install disk
and direct the installer / partitioner to that drive. Complete the install and you
should be all done....
On the ubuntu machine use gparted to resize the partitions on the 20GB hard
drive to make room for your 10GB Fedora install (you will have to unmount any
partitions on that hard drive before you can make changes). 
Then follow the instructions for the Fedora install (you should not have to create
a new swap partition as fedora and ubuntu can utilize the original swap
partition). 
Hope this helps....

---

