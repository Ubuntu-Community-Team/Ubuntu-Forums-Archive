---
title: "Install advice - no root file defined."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Jezprice on 2007-10-10
Hi folks, its been a while since i was asking question about installing Ubuntu on my new system. The reason being that i wanted to play with the live CD a bit and i like it so time to install.

I have 3 partitions on my disk - win xp, a partition for data storage leaving a 3rd partition of 40GB for Ubuntu. 

When i am installing i get to a stage; prepare disk space - where it starts asking where i want to install ubuntu. I want it on the 40gb section which shows up as FREE SPACE in the manual selection. Trouble is i keep getting a message that says " no root file system is defined" what does this message mean and how do i get it resolved? 

Also the rest of my drive is formatted as NTFS what should i use to format the ubuntu section as i dont recognise most of the options only fat32.

Thanks.


Shuttle sg33g5
Core 2 Duo 6550 1333fsb
2gb 800mhz OCZ ram
500GB Seagate 16mb sata2 hard drive
DVD R/RW 
Dell ultrasharp 20" wide screen monitor. (HDMI on shuttle - DVI connection on monitor)

---

### Post by anemptygun on 2007-10-10
I am unsure about this message... but

> Trouble is i keep getting a message that says " no root file system is defined" what does this message mean and how do i get it resolved? 


Generally most users choose the ext3 file system.

> Also the rest of my drive is formatted as NTFS what should i use to format the ubuntu section as i dont recognise most of the options only fat32.

---

### Post by Paqman on 2007-10-10
You want to divide that free space up into a couple more sections. Click on it > new partition > use as > swap (dropdown menu). Make it about 2x your RAM

To make the root partition click on “free space” again > new partition > use as > Ext3 then give it 10GB. Click on the partition you just made > edit partition > mount point > / (dropdown menu) > OK

Click “free space” again > new partition > use as > Ext3 > OK. Click on that partition > edit partition > mount point > /home (dropdown menu) > OK

That will set you up with your /home directiory on a nice big separate partition. You can put all your personal files there, and it also stores all your preferences and settings. If you ever reinstall you just format the / partition and not the /home one. All your data and settings will be preserved, just like magic!

---

### Post by ubuntu27 on 2007-10-10
> **Jezprice said:**
>  Trouble is i keep getting a message that says " no root file system is defined" what does this message mean and how do i get it resolved? 

Also the rest of my drive is formatted as NTFS what should i use to format the ubuntu section as i dont recognise most of the options only fat32.

Thanks.


[URL="http://www.psychocats.net/ubuntu/partitioning"]
Here[/URL] is a guide that I and many  others recommend to read for ["Planning a Partition"]("http://www.psychocats.net/ubuntu/partitioning")


The FileSystem should be **ext3** (could be others, but this one is recommended) for GNU/Linux.


Here is a [guide on How to install Ubuntu]("http://www.psychocats.net/ubuntu/installing") (ScreenSHots included)

---

### Post by trucker33377 on 2007-10-10
i may be wrong but a forward slash worked for me / i did a manual partition

---

### Post by bapoumba on 2007-10-12
Discussion continues there:
[http://ubuntuforums.org/showthread.php?t=573519]("http://ubuntuforums.org/showthread.php?t=573519")

---

