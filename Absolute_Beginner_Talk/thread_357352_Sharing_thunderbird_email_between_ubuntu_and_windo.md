---
title: "Sharing thunderbird email between ubuntu and windows [Resolved]"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-09
Hi 

I want to share my thunderbird email (access to) between ubuntu and windows. I got some ideas about repartitioning my drive and then moving my thunderbird profile to the (shareable) FAT 32 drive, but I failed at the point of trying to run a partition editor (QTparted said I have to run as root, and I couldn't work out how to install the others). So one good thing would be able to understand how to install a partition editor without having to reburn my SystemRescueCD.

Then I thought if I could get r/w access to my NTFS partiotion I could simply point ubuntu thunderbird at the existing windows location. But then I couldn't get any NTFS r/w facilities to work (I tried NTFS-3G). I am posting this under the newby site because I really don't understand what it means when I am told to 'unpack the file, install it and away you go) which seems to sum up the instructions of many of the things I have tried to load. I know it is my ignorance, but can anyone help?

I currently have ntfs-3g-0.20070207-RC1.tgz and ntfs-3g-0.20070207-RC1 sitting on my desktop and I don't know what to do!

Thanks

---

### Post by donmiguel on 2007-02-09
i believe this is not a good idea... 
the major problem is regarding path management... i can't recall it, but just make a diff between the file with all the settings of the linux & the windows partition.. i gave up quickly :)

windows showed empty directiories, respectively

---

### Post by ubername on 2007-02-09
> **donmiguel said:**
> i believe this is not a good idea... 
the major problem is regarding path management... i can't recall it, but just make a diff between the file with all the settings of the linux & the windows partition.. i gave up quickly :)

windows showed empty directiories, respectively

Thanks for this. I am happy that I am not the only one. But I think It should be possible either via repartiitioning or getting r/w access to the NTFS partition.

---

### Post by DJ_Peng on 2007-02-09
I actually have both my Firefox and Thunderbird profile folders on a FAT32 partition so I can use them in both Ubuntu and WinXP. I had the partition set up from when I installed because I knew I'd need data in both OSes but I haven't had a problem with accessing the data regardless of which OS I log into.

Personally I wouldn't try putting it on an NTFS partition simply due to the fact that Linux's ability to write to NTFS still has some bugs to be worked out, but putting it on a FAT partition hasn't given me a lick of problems.

---

### Post by ubername on 2007-02-10
> **DJ_Peng said:**
> I actually have both my Firefox and Thunderbird profile folders on a FAT32 partition so I can use them in both Ubuntu and WinXP. I had the partition set up from when I installed because I knew I'd need data in both OSes but I haven't had a problem with accessing the data regardless of which OS I log into.

Personally I wouldn't try putting it on an NTFS partition simply due to the fact that Linux's ability to write to NTFS still has some bugs to be worked out, but putting it on a FAT partition hasn't given me a lick of problems.

Thanks. A very basic question: How do I go about creating a FAT32 partition after I have installed? As I mentioned in the first post, I have tried runningn QTParted but it tells me I must be logged on as root.

Please when replying, don't just say 'Use GParted' or similar. I really need step by step instructions, as I have failed in my attempt to use any othe tool so far.

TIA

---

### Post by aysiu on 2007-02-10
Before you do *any* partition messing around, make sure you have backups of all your important files. Partitioning is generally safe (works about 99% of the time), but it is also a destructive tool, so you can't be too safe.

I don't think you can "just" use QTParted or GParted, as you'll probably need the partitions to be unmounted before you can resize them. If you're booted into Ubuntu... your partitions are probably mounted, as they are in use.

You'd have to do resizing from a live CD. If you have a live CD, boot it up, and then type these commands into a terminal: ```
sudo aptitude update
sudo aptitude install gparted gksu
gksudo gparted
``` This will open up the GParted partition editor. Right-click the partition you want to resize, and resize it. Then right-click the new free space and click to create a new partition of type FAT32.

Frankly, GParted and QTParted are okay most of the time, but I've had weird grayed-out options in both at one time or another. The only fail-safe partitioning tool I've found is [the DiskDrake tool on the PCLinuxOS CD.](http://ubuntuforums.org/showthread.php?t=114142)

By the way, to share your Thunderbird profile, you'd have to shortcut C:\Documents and Settings\ubername\Application Data\Thunderbird and /home/ubername/.mozilla-thunderbird (also known as ~/.mozilla-thunderbird) to the profile on your shared FAT32 partition.

Also, keep in mind that the native Ubuntu Thunderbird is ~/.mozilla-thunderbird, but the Mozilla Thunderbird (from the actual Mozilla website) is ~/.thunderbird.

---

### Post by Jussi01 on 2007-02-10
> **ubername said:**
> Hi 

I want to share my thunderbird email (access to) between ubuntu and windows. I got some ideas about repartitioning my drive and then moving my thunderbird profile to the (shareable) FAT 32 drive, but I failed at the point of trying to run a partition editor (QTparted said I have to run as root, and I couldn't work out how to install the others). So one good thing would be able to understand how to install a partition editor without having to reburn my SystemRescueCD.

Then I thought if I could get r/w access to my NTFS partiotion I could simply point ubuntu thunderbird at the existing windows location. But then I couldn't get any NTFS r/w facilities to work (I tried NTFS-3G). I am posting this under the newby site because I really don't understand what it means when I am told to 'unpack the file, install it and away you go) which seems to sum up the instructions of many of the things I have tried to load. I know it is my ignorance, but can anyone help?

I currently have ntfs-3g-0.20070207-RC1.tgz and ntfs-3g-0.20070207-RC1 sitting on my desktop and I don't know what to do!

Thanks

For the ntfs 3g thing, I would suggest following this tutorial, its quite simple and nice to follow:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g)

Hope that helps you.

Cheers

Jussi

---

### Post by ubername on 2007-02-11
All done, via a FAT32 partition. Thanks all.

---

### Post by DJ_Peng on 2007-02-11
Awesome, uber. Don't forget, you can do the same with your Firefox profile as well. Probably for whatever your preferred browser is, too.

---

### Post by ubername on 2007-02-11
> **DJ_Peng said:**
> Awesome, uber. Don't forget, you can do the same with your Firefox profile as well. Probably for whatever your preferred browser is, too.

Done! In fact I did it for firefox first because I reckoned it was less risky to lose my firefox settings than my email.

Thanks again all.

---

### Post by DJ_Peng on 2007-02-11
Good call, and I hope you backed everything up first, just to be on the safe side. You usually don't need the backup, but you never know.

---

### Post by ubername on 2007-02-12
> **DJ_Peng said:**
> Good call, and I hope you backed everything up first, just to be on the safe side. You usually don't need the backup, but you never know.

Thanks. As I have worked in IT obviously I just went ahead and did it, then when it worked I took a backup because I realised what a risk I had taken!

---

### Post by DJ_Peng on 2007-02-12
Yeah, I've done that a time or two myself. I"m trying toget better about backing up before major changes.

---

