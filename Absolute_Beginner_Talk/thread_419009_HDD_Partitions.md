---
title: "HDD Partitions"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by THEnumber337 on 2007-04-22
Hello,

I've been interested in running Ubuntu for a while now. I've been trying it out a little in VMware. Now since Feisty is out I want to install it natively in a dual boot with my XP Home. I currently have my HD partitioned into 3 separate partitions. Would it matter which one I installed Ubuntu to?


Thanks

---

### Post by RobsterUK on 2007-04-22
You would need to create a new partition for Ubuntu during the install.

What is your existing partition setup? what file systems and operating systems are you using on them?

---

### Post by THEnumber337 on 2007-04-22
> **RobsterUK said:**
> You would need to create a new partition for Ubuntu during the install.

What is your existing partition setup? what file systems and operating systems are you using on them?

My C drive is 20GB and houses the OS and drivers, D drive is 20GB and hosts just various programs, and E Drive is 110GB and holds my media and the like.

I'm just using Win XP Home.

---

### Post by kevinf311 on 2007-04-22
I dual boot Linux and windows and have my partitions set up as so:

[--~25GB XP ntfs--][--------~75GB /home ext3--------][--~15GB / ext3--][2GBswap]

The plus to having a separate /home partition is that if you mess up your root file system you can reinstall without losing your documents and settings. There is a windows utility that allows for read/write to ext2 partitions (the difference between 2 and 3 mainly being a Journaling system) called [FS-Driver]("http://www.fs-driver.org/") that I use.

With this set up I have all of my documents, music, video files, etc in the /home partition so that both XP and Linux can access and manipulate them.

Hope this helps some.

[edit]
It might be a good idea to back up your data. 

There is reasonable support for ntfs read/write in Linux now, so you could do what I did but inverting the OS control of the media partition.

---

### Post by THEnumber337 on 2007-04-22
Yeah, thanks for the quick responses, they definitely help.

I've already backed up everything. Could I just delete the last partition I have that is 110GB and then set up Ubuntu on there with home and swap and all that?

---

### Post by RobsterUK on 2007-04-22
> **THEnumber337 said:**
> My C drive is 20GB and houses the OS and drivers, D drive is 20GB and hosts just various programs, and E Drive is 110GB and holds my media and the like.

I'm just using Win XP Home.

Assuming you have some free space on the 110GB partition you can ask the Ubuntu installation to resize that partition and use the free space to set up the partitions it needs (install and swap partition)

---

### Post by THEnumber337 on 2007-04-22
> **RobsterUK said:**
> Assuming you have some free space on the 110GB partition you can ask the Ubuntu installation to resize that partition and use the free space to set up the partitions it needs (install and swap partition)

Yeah. I actually already backed up all my files and everything and deleted it all from the partition already. :)

---

### Post by RobsterUK on 2007-04-22
> **THEnumber337 said:**
> Yeah. I actually already backed up all my files and everything and deleted it all from the partition already. :)

Oh right, well then deleting that partition and installing Ubuntu in the space like you suggest is probably good way to go about it.

You said you tried Ubuntu in VMWare but its probably worth trying it out booting from the CD just to check how it deals with recognising your hardware

---

