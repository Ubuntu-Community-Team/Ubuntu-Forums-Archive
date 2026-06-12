---
title: "Installation Help"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by new2linux2009 on 2006-03-24
Hi, I'm trying to install dual boot for Windows XP professional and Ubuntu Breezy Badger v. 5.10. Also, I created a 10 GB partition on a 40 GB hard drive with Partition Magic and I was wondering how to install Ubuntu on this partition. The only instructions I could find created a new partition, but I am all ready one step ahead of the game... PLEASE guide me through the install...I would reallly like to start using Ubuntu today...I am sick of windows...but will need it for school because I go to a Laptop school](*,) :-D

---

### Post by pooler on 2006-03-24
It's likely that the partition you made with Partition Magic can't host a gnu/linux installation. What you need to do, is to select the option "Do the partitions manually" (those are not the exact words, but I think it's the last option, or the one over it). Then highlight the partition you've made, delete it and create TWO new partitions . The first one should be in "Linux" format (ext3, xfs or reiserfs), and the second one should be "Linux Swap". The size of the second partition depends on the system memory (if you have ~256MB or more of RAM you should get by with ~300MB, if you have less, the swap partition should be larger). The first one should use the rest of the disk.

---

### Post by Sef on 2006-03-24
> I'm trying to install dual boot for Windows XP professional and Ubuntu Breezy Badger v. 5.10.

Follow this excellent tutorial to dual boot:

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")


>  I created a 10 GB partition on a 40 GB hard drive with Partition Magic

There have been reports of many problems using Partition Magic.  With the install disk, there is a partioner that will do just fine.

---

