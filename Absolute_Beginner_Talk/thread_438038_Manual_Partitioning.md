---
title: "Manual Partitioning"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by jopv on 2007-05-09
I have a new Thinkpad Z60T with an 80 GB hard drive. I tried to install Ubuntu using the standard partitioning option (1st Guided option for dual boot) but it didn't work. It then offered me the manual option. I would like to dual boot with Windows but it looks like I have to do it manually.

I'm a newbie to Linux and I don't know much about partitioning except for theory. I don't know the space allocations for different partitions.  Is there any standard, "easy" Ubuntu guide on partitioning especially on how to allocate the right amount of space for the different partitions?

I need all the help I can get.

---

### Post by Inxsible on 2007-05-09
Check this out
 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by mejy on 2007-05-09
It's not too hard - you'll want to set as much as you want for Windows.  You can the optionally add a partition of around 100 MB and format it Ext2 - you'll need to mount it at /boot.  You'll most likely want a partition around twice the size of your RAM for a swapfile, which you'll need to format as swap and mount as a swapfile.  You can use the rest of your partition for your root partition - you should probably format it Ext3, and you need to mount it as the root partition - at '/'.  If you need more detail, feel free to post back.

---

### Post by crimesaucer on 2007-05-09
Read this guide for manual partitioning.

It has easy to follow directions with screenshots for a text install using the "Alternated" CD. It's for a dual boot of Windows Xp (ntfs), and a FAT32 partition for file transfer from ubuntu to Windows Xp:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

and here is the home page of it for more info on different installs and ways to install: 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by jopv on 2007-05-11
Thanks a lot to all of you for providing information.

I'm surprised that Ubuntu does not have standard step-by-step documentation on the types of partitioning.  Such things are vital if you want people to move to Linux.

---

### Post by mikewhatever on 2007-05-11
Actually, it does, see the link below, but here is the community support forum, so nothing is standard.
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

For the basic set up, you'll need to create two partitions, root and swap. Swap is somewhat similar to the page file in Windows, and should be sized as 1.5-2xRAM or what your needs require. Root is where Ubuntu is installed, so it should be at least 3 BG, but something like 10 would be better. It also needs to be formated as ext3 and mounted as /.

Good luck, and welcome.

---

### Post by jopv on 2007-05-11
Is swap a primary, logical or extended partition?

---

### Post by mikewhatever on 2007-05-11
It does not matter. Any Ubuntu partition can be either primary or logical. An extended partition is created to contain logical ones.

---

