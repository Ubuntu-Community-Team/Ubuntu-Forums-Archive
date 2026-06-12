---
title: "Dual booting Linux and Xp?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Yautja_Ender on 2006-01-06
Okay... i have a windows partition on one drive allready with all my data and music on it... is there anyway to set up ubuntu on my other drive and be able to dual boot into uduntu and windows xp without deleting my hard drive with windows on it?... i just recently installed ubuntu on my new drive so im not that worried about loosing anything. It Also might be appropriate to say that i have Sata...

thanks

---

### Post by iand675@gmail.com on 2006-01-06
Yeah you can do that, as a matter of fact the grub boot loader is able to set it all up for you. But I would personally back up all of your stuff just in case. It's generally reliable, but sometimes an irregular bios or hardware config issue can screw it up.

---

### Post by Yautja_Ender on 2006-01-06
cool, thanks... yeah i would have allready done it but im waiting till tom. when im back at school and have my windows disc with me... by the way... is there a way to change my current setup of ubuntu so that it gives me the option of dual booting without erasing it and starting over?

---

### Post by Sef on 2006-01-06
Yes, you can set up a dual boot with no problem.

1) Install Windows first

2) When it gets to partitioning, use 'manually partition' (similar words-it's the bottom option.)  Below is from a previous post of mine:

>  Re: Partitioning Problems - 5 Days Ago 
I) If there is no free space on the disk, do this:

A) Highlight the partition you want to shrink. 

B) Highlight the disk size. 

C) Erase the numbers on the screen and write in the new size of the partition - XX.X GB . 

- Don't forget to put GB

4) Click on the button. (I think it says 'OK'.)

5) Then click on 'Done Partitioning This Disk' (or something similiar, it's the top option.)

II) Two Partitions Now

A) One which says NTFS and one that says Free Space.

1) NTFS is the XP partition
2) Free Space can used to set up Ubuntu Linux.

-) It's a good idea to maually partition, and set up a /home directory, so when you upgrade Ubuntu, your files and settings won't be overwritten.

3) Read this first before installing.   It explains with pictures how to install a dual boot.  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

