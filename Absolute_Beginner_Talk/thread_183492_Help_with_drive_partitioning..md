---
title: "Help with drive partitioning."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-05-28
I did a quick search of the recent topics but I couldn't find this issue addressed. Google yielded partitioning help, but it didn't give me quite the info I need. 

I want to set my system up with Linux as well as Windows, and I'm trying to follow the procedure on the website for setting it up. I burned an Iso, and then restart while booting from the CD drive. Then I follow the prompts, hit enter when appropriate, etc, and then I get stuck at the part where it wants to partition my drive. I have about 52 gigs on my HDD, and just under 20 are actually being used.

I ran O&O Defragger and it really compacted it down (much better than the windows one does), but the boot disk still says that there's not enough continuous space to make a big enough partition (I figure because of the unmovable system files). Then it asks if I want to do it manually, but I really don't know what option to choose and I'd rather not accidentally erase a whole bunch of stuff. I have most of my files backed up (All my music and games and stuff fit on one DVD+R), but if anything happens to windows itself I'm going to have to go dig around for a few hours to try and find my windows disk.

I can get a screen shot of where I'm stuck, but I'll have to use my digital camera since C&Ping it into paint won't quite work under these circumstances.

---

### Post by lukew on 2006-05-28
[QUOTE=Amablue]I did a quick search of the recent topics but I couldn't find this issue addressed. Google yielded partitioning help, but it didn't give me quite the info I need. 

I want to set my system up with Linux as well as Windows, and I'm trying to follow the procedure on the website for setting it up. I burned an Iso, and then restart while booting from the CD drive. Then I follow the prompts, hit enter when appropriate, etc, and then I get stuck at the part where it wants to partition my drive. I have about 52 gigs on my HDD, and just under 20 are actually being used.

I ran O&O Defragger and it really compacted it down (much better than the windows one does), but the boot disk still says that there's not enough continuous space to make a big enough partition (I figure because of the unmovable system files). Then it asks if I want to do it manually, but I really don't know what option to choose and I'd rather not accidentally erase a whole bunch of stuff. I have most of my files backed up (All my music and games and stuff fit on one DVD+R), but if anything happens to windows itself I'm going to have to go dig around for a few hours to try and find my windows disk.

I can get a screen shot of where I'm stuck, but I'll have to use my digital camera since C&Ping it into paint won't quite work under these circumstances.[/QUOTE]
From the sound of this you have one primary dos partiion and nothing else. I think what it is saying is there is not enough free space to make a new partition. FDisk can not resize a primary dos partiion, which is what you need to do. You need a tool to do this for you.

I used to use parition magik when i used to use windows, which is a comercial buy, this always seemed to work well. I can not vouch for free applications which can do this, but I am sure there are some good ones out there. Unfortunalty the disk management tool can not resize a primary dos parition.

You can remove all paritions, make multiple paritions and then reinstall every linux and windows. Perhaps you could just reinstall windows and leave the lattter. 

I hope this helps.

Luke





I hope this helps.

---

### Post by Amablue on 2006-05-28
I'm a bit unclear. If I partition, do I have to reinstall windows, or can I just move everything together with Partition Magic and then set up a second partition without having to mess with Windows? If at all possible, I'd like to leave windows alone, I might have trouble finding my disk if anything happens to it.

---

### Post by lukew on 2006-05-28
[QUOTE=Amablue]I'm a bit unclear. If I partition, do I have to reinstall windows, or can I just move everything together with Partition Magic and then set up a second partition without having to mess with Windows? If at all possible, I'd like to leave windows alone, I might have trouble finding my disk if anything happens to it.[/QUOTE]

It is quite possible to resize a primary partiion.

You can do this with Parition Magic. and I am sure you might beable to find something which is free which can also do this.

Do you have only one parition on this drive? Do you have another drive you could use? It may be easier to buy a second hard drive.

I hope this helps.

Luke

---

### Post by carverj on 2006-05-28
yes, if you partition with the boot disk you'll have to reinstall Windows. What I did was installed NTFS first (to the beginning fo the disk) and then used the Ubuntu installer to divvy up the remaining space (including a swap partition and believe i could even resize partitions on my slave hard drive- don't quote me)
That way you can install GRUB to the MBR (master boot record) and it will load windows or Linux.

---

### Post by Amablue on 2006-05-29
[QUOTE=lukew]You can do this with Parition Magic. and I am sure you might beable to find something which is free which can also do this.

Do you have only one parition on this drive? Do you have another drive you could use? It may be easier to buy a second hard drive.[/QUOTE]

I'm on a laptop with only one drive. I'm trying to find a free partitioning tool now, since I don't feel like paying for a commercial program, but I'm making sure to check reviews and stuff before I buy it because I want to be absolutely sure it'll work.

---

### Post by jimrz on 2006-05-29
[QUOTE=Amablue]I'm on a laptop with only one drive. I'm trying to find a free partitioning tool now, since I don't feel like paying for a commercial program, but I'm making sure to check reviews and stuff before I buy it because I want to be absolutely sure it'll work.[/QUOTE]

PartitionMajik does work. If you do not already have PM, the installer's partitioner can resize your ntfs partition creating room for your ubuntu. Look[[COLOR="Sienna"]**_ here_**[/COLOR]]("http://users.bigpond.net.au/hermanzone/") for an excelent guide, which is for breezy install. If you are doing dapper, I did mine with the alternate install cd, it is similar enough to get you through without problems. In particular, the partition section is nearly identical.

---

### Post by decaturcomp on 2006-05-29
and, it seems like you have to make the new ubuntu partition less than 8 gb or grub makes trouble before getting to the boot part. then make a swap file (normallly twice the RAM, right?) all with PM and you can do a slick easy install that actually works.

---

### Post by RRS on 2006-05-29
I've heard various reports of problems between Partition Magic and Linux, though I haven't used it myself. (don't like to pay for software either)

Gparted has a live cd which works well for partitioning and is also available as an additional aplication in Ubuntu.

Overall though I have to agree with jimrz and highly reccommend using [URL="http://users.bigpond.net.au/hermanzone/index.htm"]Herman's guide.
[/URL]

I also see he's added this note to his homepage;
> NOTICE: This website pertains to installing Ubuntu 'Breezy Badger 5.04' and not the newest version 'Dapper Drake 6.06' which is due to be officially released very soon.
             It will be some time (if ever) before this website will be updated.

For help with Dapper Drake 6.06 install from the new Dapper Live/Install CD, I recommend Aysiu's website, [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) and in particular, this page, [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
And while you are there check out the rest of Aysiu's site too, you'll find lots of other good information there.

The graphical installer that I used for Dapper has changed a little from these Breezy install examples, but is still quite similar. 

Both of the links he provides are also quite good.

Don't hesitate to ask if you have any further questions, we're all learning here.

---

### Post by Amablue on 2006-05-31
Okay, so I found my Windows disk, I backed up all my files, and plunged in. After messing around with the partitioner, I decided to go with 20 GB for Ubuntu and 37.5 for Windows, with a 2.5 GB swap drive. It seemed to work at first. I got my first taste of Ubuntu. I messed around with the interface for a while, played some of the games (ironically, the first game I played on my new non-windows OS was minesweeper) and just tried to get a feel for the system. Before I started to really start customizing, I figured it would be good to get Windows back up, since I just flattened it in my partitioning. 

But here's what I noticed. I was hoping Ubuntu would divvy up the partition however it needed, but it seemed that it took the 37.5 space and used that for my /home, I think (Still trying to understand/get used to exactly how Ubuntu sorts stuff). So when I tried to reinstall windows, I think it took that portion, and now I can't figure out how to get Ubuntu running again. 

I imagine I might have to re-install both again, which is no problem. I just want to know what I should do different this time. What I'm going for is roughly a 20/40 split (but I took 2.5GB off the windows partition for the swap drive). What do I do to get Ubuntu to just take up the 20, and how do I set it up so that I can choose my OS when I boot up?

Herman's guide has been useful, but it's a bit hard to follow sometimes, and I feel I may just be overlooking the answer to my problem. He just seems to gloss over certain things that I'd need to ask about (but that's what the forums are for :-D ) If anything here is covered in detail and I've overlooked it, just point me to it. 

And you guys have been a great help so far, thanks.

---

### Post by Amablue on 2006-05-31
I suppose posting in the middle of the night tends to give the thread too much time to fall off the front page ](*,)

---

### Post by aysiu on 2006-05-31
Are you really trying to tell me Herman's guide glosses over stuff?

Look at this page:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Every single step has a screenshot and an explanation.

The easiest way to do a dual boot is to install Windows on the whole drive and then shrink it with the Ubuntu installer and install Ubuntu after Windows.

I don't think Ubuntu will ever create a separate /home partition unless you tell it to (unfortunately). /home partitions are great things, but when you tell Ubuntu to use the whole disk (I've tried this before), it just assumes you want only two partitions: swap and /

---

### Post by carverj on 2006-06-06
how is your partitioning going? It is very confusing when you first try it!

```
What do I do to get Ubuntu to just take up the 20, and how do I set it up so that I can choose my OS when I boot up?

```

Yes, install Windows to the first 40 Gig or however much you like, Then install Ubuntu install  cd, creating partitions of various sizes (however you like to divvy it up). The herman zone site does guide you through this even if it does seem confusing at first.
At the end of the install is the option to place GRUB (bootloader) on the MBR.
go for it and youll be able to dual boot.

cheers

---

