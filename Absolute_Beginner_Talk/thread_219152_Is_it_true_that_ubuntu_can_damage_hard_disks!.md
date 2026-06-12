---
title: "Is it true that ubuntu can damage hard disks!"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-07-19
I was chatting to a (socalled)'computer expert' and he was saying that he had gone back to windows after burning out several hard disks with ubuntu. Something about them not powering down when not in use but constantly spinning.

It made me worried because ive lost  2 disks recently (within 2 years) since switching and its only happened once in my 15 years of PCs with dos & win

Is this true :-| can there be any wrong settings that can do this??

Please put my mind at rest.

While im at it, is there a defrag & disk care util?

---

### Post by wahman143 on 2006-07-19
Any operating system can destroy a hard drive given some time.  Back in the old days of linux, if you did not configure hdparm (hd parameter program) properly, you could in fact kill a drive...however, linux has progressed a long way and I've found that my drives last longer when running linux.  A drive CAN be hosed if you don't unmount it properly or sometimes if you lose power...but typically it can be fixed.

People who are scared of Linux think it destroys hardware because they do not understand the commands and usage properly.  

There is no defrag util - the filesystems that linux uses are all more efficient than FAT or NTFS, and therefore do not frag in the same way.  Reiserfs is the only exception, but even then it's nowhere near any of the windows fs in terms of fragging.

What other kinds of utils are you interested in?

Cheers,
W.

---

### Post by steve.horsley on 2006-07-19
I don't believe this is possible with desktops. Some laptops may have incompatible hardware that prevents the OS power management from spinning down the disk to save battery, but only a second design flaw would allow disks to "burn out" just because they are constantly spinning.

---

### Post by mattisking on 2006-07-19
I'll try... I haven't heard of this but it's kind of hard for me to imagine. Your hard disk spinning isn't really controlled by Ubuntu. Some kind of process that was large enough to use a large amount of virtual memory... or one that constantly accesses the drive? If a program like that existed... I'd say it would be something like Beagle but I still seriously doubt it. Disks are much smaller these days so the chance of something going wrong is much higher. Also, unfortunately, some disks just aren't as well made as they once were. That's far more likely to be the culprit. 

As for as disk defragging, ext3, unlike FAT/FAT16/FAT32/NTFS rarely, if ever, needs defragmenting. The only way you'd probably ever need to worry about something like that is if you were running something like a file server. There are, however, a set of defrag utilites depending on the structure you select (default is ext3). Once setup and going, enable the universe repository (pretty sure that's where it is) and search/install the package "defrag" from Synaptic. Of course, you have to be able to take the drive you want to defrag "offline" before you can do it and on that note, I'm out of my league.

---

### Post by wahman143 on 2006-07-19
> **mattisking said:**
> Of course, you have to be able to take the drive you want to defrag "offline" before you can do it and on that note, I'm out of my league.
Best practice is to boot to a livecd and run utils on it there, while the disk is not mounted.  NEVER RUN DISK UTILS LIKE FSCK ON A MOUNTED DISK!!!

Cheers,
W.

---

### Post by KingBahamut on 2006-07-19
I think the validity of this statement comes suspect, at least to me. So, no, I dont believe that Ubuntu (or any other Linux Distro) can damage a harddrive. There are whole systems that run linux that have relatively incredibly high uptimes, and incredibly low maintenance costs. 

To answer your last question, No. 

Fragmentation primarily occurs in OS's that dont possess a decent journaling filesystem. Have to remember in the case of a FAT or NTFS envoirment, you have a series of blocks being moved, place, and replaced. The locgical order that this is done is not always so logical, as the contiguous nature of files is not so solidly arranged together. 

in the EXT2 file system you could use e2defrag(volume has to be offline) to defragment your system. EXT3 I dont believe has such a tool, but ReiserFS might.

---

### Post by dgrafix on 2006-07-19
Ok thanx guys, i can now argue my case ;)

---

### Post by Brunellus on 2006-07-19
I'm going to call BS on this.  If Linux were so hard on hard disk hardware, why haven't I heard much complaining from guys who run server farms?  They have many more hard drives used much more intensively than your home computer...and yet I'm simply not aware of any greater incidence of physical hard drive failure.  If your "expert" friend is so convinced, I'd like to hear the technical explanation--and preferrably read relevant studies.

There are several things that YOU can do, however, that will not be happy for your hard disk.  None of them are inherent to Ubuntu....

The most obvious involves dual-boot systems, where users insist that they must have WRITE as well as read access to their Windows NTFS partition.  That's not very safe at the moment, and has been known to cause irreparable filesystem corruption on NTFS partitions.  You have been warned.

As far as defragmentation:  the ext3 filesystem (ubuntu default) has no real defragmentation utilities.  Generally, most people don't believe fragmentation to be a problem with ext3 (and ReiserFS3), as they are in FAT32 and NTFS.  Again, take your cue from teh server farmers--if the server farmers aren't defragmenting, that might tell you something.

---

### Post by qdvubun on 2006-07-19
never happened before for me, the only 1 time I killed a drive was because didn't mount properly and didn't know what I was doing, and that was when I play with dos mode, without any OS.

---

### Post by orb9220 on 2006-07-19
You can be safe in the knowledge He is not talking with any knowledge that has any basis in truth.

Tell him for me that he is full of "Horse Patutee's". That is techie talk he should at least understand.

---

### Post by Sonofmoog on 2006-07-19
I'm going to agree on some points of this thread and disagree on others.  I agree that defrag in Linux is akin to carrying coals to Newcastle; it isn't necessary.  There can be exceptions I am told, but in average home use, no.

Where I disagree is in the claim that Ubuntu will not harm hardware.  There is an old maxim in the trades that software cannot destroy hardware.  It is baloney.  I've lost entire harddrives on several occasions, both in Windows and Linux.  

I am told by those whose opinion I respect that Linux works the hardware harder than Windows, and generally I agree with this.  I can transfer files over the network between two Linux PC's faster than I can copy them to logical partitions on the same PC in Windows.  This performance comes at a price, and the price is higher wear and tear, and higher risk of problems down the road.

---

### Post by Brunellus on 2006-07-19
> This performance comes at a price, and the price is higher wear and tear, and higher risk of problems down the road.

The real question is to what extent is this even a consideration for the average home user?

---

### Post by arkangel on 2006-07-19
giving my opinion ...

some servers are working 24/7 and those are using linux,  how  you ever heard this is a particular issue in such servers? ....

---

### Post by Kilz on 2006-07-19
If it were true that Ubuntu kills hard drives, there would be a ton of "Help My hard drive died" posts.

---

### Post by mcduck on 2006-07-20
Hard drives are supposed to spin all the time. Stopping them when not used is just an extra power saving feature, mostly used in laptops. Those disks are built to spin at constant speed continuously for years. If this breaks the disk, it's because there is something already wrong with the disk, or there isn't sufficient air flow to cool the disk.

---

