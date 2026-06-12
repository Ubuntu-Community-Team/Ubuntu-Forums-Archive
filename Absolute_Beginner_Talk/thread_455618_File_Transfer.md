---
title: "File Transfer"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by xkcd on 2007-05-26
During the fifth step in the installation process the LiveCD checks for any Documents and Settings folders that can be transferred. Unfortunately none of my documents from Windows were listed. I haven't used any program to try to make the files transferrable (mainly because I don't know if one exists), and I was hoping that one of you Linux gurus could help me out. All I need is advice on how to transfer files from WIndows to Ubuntu. Many thanks!

---

### Post by taurus on 2007-05-26
What files you need to copy from Windows to Ubuntu?  You need to mount your Windows partition first before you can access it and if it is ntfs filesystem, then you need to use ntfs-3g driver so you can write to it if you want to.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by xkcd on 2007-05-26
The files that I need to transfer are mostly media (photos, music, videos, etc.). BTW, I just want to point out that this is my first Linux distribution, so I may have more questions in the future.

Ok, these command lines, must I use them in the LiveCD test of the Linux or in the Windows command prompt? (don't laugh at my noobness TT^TT)

---

### Post by taurus on 2007-05-26
Have you installed Ubuntu on your computer, harddrive, and if you have, which release did you install?

---

### Post by xkcd on 2007-05-26
I have Feisty but it is not installed because I feared losing my data. Do I need to partition my hard drive?

---

### Post by taurus on 2007-05-26
If you haven't installed Feisty on your harddrive, then what do you mean by transferring files from Windows to Ubuntu?  You first need to install Ubuntu onto a harddrive before you can transfer files from Windows over to Feisty.  

If you only have one harddrive, then you need to resize it to make room at the end for Ubuntu.  And of course, always backup your data before you decide to resize your harddrive just in case you click the wrong button or else bye-bye data.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by xkcd on 2007-05-26
Ok. Sorry, I was under the assumption that none of that was needed. Thank you for listening to my cry for help!

---

### Post by Pizzarth on 2007-05-26
yes, you need a separate partition(ext3,) for ubuntu unless you work some magic, metaphorical or not. you can install it fine on that seperate partition without trouble. the only "dangerous" thing about the install is resizing your windows partition, if need be. But I didn't have a problem with that. My advice would just be to use a seperate harddrive or online storage utility to back up the media, though the online storage would take a while to upload to. You can't just copy it over through the livecd as far as I know, it's all running in memory and off the drive. 

so, yea, create a swap partition too. it's like what your windows uses without telling you. ~750 megs of each partition in windows is taken up by that. It's just a place on the harddrive that acts as memory, but is slower.

usually the information is safe, but it's always smart to back things up, as you'll find soon enough. (usually through messing with xorg.conf)


heh you posted a minute before I finished htis one.

---

### Post by xkcd on 2007-05-26
All right then, I'll find some way to back up my media and then create a partition for Ubuntu. Now one quick noobish question (it's my first time ever actually doing this): Could you explain the swap partition again? I'm not sure exactly what it is.

---

### Post by Pizzarth on 2007-05-26
no problem

very basic computer workings: Processor does stuff, commits calculations :) and deals with...well..just about everything mainly through I think the proper name is apu, arithmatical processing unit. it stores the numbers in registrars were it takes a bout 1-2 clock cycles (that's the mhz/ghz rating on processors, the flip of the lectricity on and off) to get to. Second is the L1 cache, a special kind of memory built in ot the processor, usually there. it's SRAM, more expensive, and faster than normal DRAM (static vs. dynamic random access memory) On the memory stick, it's mostly DRAM with some SRAM built in as L2 cache. L1 and L2 have no signifiance beyond the one and two. p.s. memory takes about 25 clock cycles I think. When the memory is too full, so to speak, it needs somewhere else to store numbers, in here is the job of the hard drive, specifically the swap partition. it's sortof like, "virtual memory" hdd access takes about a 1000 clock cycles, from what I remember. But when you have processors going at billions of clock cycles a second, it doesn't really matter. usually people recommend the swap to be 2 times the size of your memory. I've got 512 mb of memory, with a 1 gig swap. I think some say 1.5x works well too, I don't know about the numbers.

looking back at it, maybe not very basic, but simplified.

---

