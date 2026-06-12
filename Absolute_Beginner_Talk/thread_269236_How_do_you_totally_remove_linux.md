---
title: "How do you totally remove linux?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by lee101 on 2006-10-01
i need to remove ubuntu,

does anyone no how 2??

help

---

### Post by meng on 2006-10-01
What are you removing it from/for? An existing dual boot system (say with XP)? A multi-boot, multi-Linux-distro system? Or a single-OS system? Or do you just want to overwrite the existing root partition by installing a different OS/Linux distro over the top of Ubuntu?

---

### Post by IYY on 2006-10-01
Just install Windows. It probably won't even ask you.

---

### Post by devils_casper on 2006-10-01
Hi !

if there is **ONLY** ubuntu installed then you can wipe HardDisk. boot up through Ubuntu CD and in terminal type this command...

sudo dd if=/dev/zero of=/dev/hda bs=521 count=1

this will erase partition table and your HardDisk will be Blank as new.




casper

---

### Post by meng on 2006-10-01
> **IYY said:**
> Just install Windows. It probably won't even ask you.
> **devils_casper said:**
> Hi !
if there is **ONLY** ubuntu installed then you can wipe HardDisk. boot up through Ubuntu CD and in terminal type this command...

sudo dd if=/dev/zero of=/dev/hda bs=521 count=1

this will erase partition table and your HardDisk will be Blank as new.
Hence the importance of specifying what exactly your needs are.

---

### Post by lee101 on 2006-10-01
i have windows and ubuntu installed, they are both on seperate hard drives

---

### Post by bigken on 2006-10-01
you can use any program to format the linux partions and if you cant boot to windows just boot from the winxp cd go to repair console at the prompt type fixmbr then fixboot then exit the pc will reboot and your into windows ;)

---

### Post by Speedycat on 2006-10-01
Just wipe the hard drive with Ubuntu on it.

---

### Post by lee101 on 2006-10-01
can i wipe my hard drive with ubuntu on with the partition magic

---

### Post by bulldog on 2006-10-01
> **lee101 said:**
> can i wipe my hard drive with ubuntu on with the partition magic

Absolutely..............:D

---

### Post by devils_casper on 2006-10-01
you can use Partition Magic but i dont recommend it to anyone coz its a bit problematic. best way is Unplug WINDOWS harddisk, boot up through Ubuntu CD and execute 'dd' command i posted in post #4



casper

---

### Post by bulldog on 2006-10-01
> **devils_casper said:**
> you can use Partition Magic but i dont recommend it to anyone coz its a bit problematic. best way is Unplug WINDOWS harddisk, boot up through Ubuntu CD and execute 'dd' command i posted in post #4



casper

Tell me about it please,what's wrong with it??

---

### Post by bigken on 2006-10-01
download [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD its a simple but very good pationer ;)

---

### Post by bigken on 2006-10-01
another way would be to run repair console 1st and the fixmbr/fixboot/exit  and just use windows to format the drive ;)

---

### Post by mitch1 on 2006-10-01
is it easier to use partition magic, if so how do u remove ubuntu using partition magic

---

### Post by devils_casper on 2006-10-01
[QUOTE=bigken]another way would be to run repair console 1st and the fixmbr/fixboot/exit and just use windows to format the drive [/QUOTE]


if there is only Linux in HardDisk then windows CD wont even BOOT UP.
regarding Partition Magic, a lot of problems... it tries to capture windows start up processes and on booting up ( after every fixing through it ) PM try to configure disks/partitions itself. most of time, it fails and leave a blue screen...




casper

---

### Post by bigken on 2006-10-01
(if there is only Linux in HardDisk then windows CD wont even BOOT UP)

Tell me why ?

---

### Post by bulldog on 2006-10-01
> **devils_casper said:**
> if there is only Linux in HardDisk then windows CD wont even BOOT UP.
regarding Partition Magic, a lot of problems... it tries to capture windows start up processes and on booting up ( after every fixing through it ) PM try to configure disks/partitions itself. most of time, it fails and leave a blue screen...




casper


Hmmmm,have used it for several years now and had never and I mean never any issue with Partition Magic.

Maybe I was just lucky :cool:

---

### Post by devils_casper on 2006-10-01
OR may be a few of friends and me are unlucky... :)
it works fine with windows 98.. problems in NTFS and other NT based OS' !




casper

---

### Post by lee101 on 2006-10-01
i will not use partition magic the been as it creates problems:( 

what is the easiest and quickest way.

---

### Post by bigken on 2006-10-01
Tell me why you cant boot from a winxp cd if you only have linux on the drive ? :-k

cos that is cobblers ;)

---

### Post by crokett on 2006-10-01
> **lee101 said:**
> 
what is the easiest and quickest way.

What was posted before:

Boot from the winxp cd go to repair console at the prompt type fixmbr then fixboot then exit the pc will reboot and your into windows.  From there use disk manager to reformat the HHD that has linux on it.

---

### Post by devils_casper on 2006-10-01
[QUOTE=bigken]Tell me why you cant boot from a winxp cd if you only have linux on the drive ? [/QUOTE]

you should try yourself. even fdisk wont work ! 




casper

---

### Post by bigken on 2006-10-01
so your telling me you cant boot from a cdrom :-k

---

### Post by lee101 on 2006-10-01
thanks to every1 who replied in this thread much appreciated

---

### Post by bigken on 2006-10-01
> **devils_casper said:**
> you should try yourself. even fdisk wont work ! 




casper

you must be doing something sadly wrong my son ](*,)

---

### Post by ubu-jazzguy on 2006-10-01
new user since yesterday.
I have a similar question. I just installed ubuntu 6.06 for 64 bit systems. I downloaded ubuntu at work and was'nt paying attention to what version i got.

 I got it installed and everything but I really don't want the 64 bit version. So i have 3 hdd. 1st- a 100GB sata with win 64 on it. 2nd drive -a 160 GB in two 76.* GB partitions. 

One partition is win 32 and the other ubuntu. If i just wipe the ubuntu partition is this going to screw up booting to the other to win partitions?? 

should I  back up my win partitions first? I have the 32 bit ubuntu downloaded and want to install it to the partition i have the 64 bit ubuntu on right now.

the 3rd hdd is just for storing movies and music etc. nothing booting off of it.  Thanks a Lot.

---

### Post by gn2 on 2006-10-01
> **bulldog said:**
> Hmmmm,have used it for several years now and had never and I mean never any issue with Partition Magic.

Maybe I was just lucky :cool:

No, it isn't just you, Partition Magic is well named.

I've found it to be- as we scots say- MAGIC!

---

### Post by gn2 on 2006-10-01
Moderators, can we please have a sticky thread about people making long posts in one paragraph that just goes on and on, with no line breaks, or gaps between, because I find it can become difficult to understand also it's tiring on the eyes when you have to concentrate hard on where you are in the text and it's hard to refer back to something earlier in the text because it's not spaced out and I just find it hard to find if you know what I mean. I'm sure I'm not the only one who finds it a struggle to read posts like this where there aren't even gaps between the paragraphs. Don't want to come over as a bit of a grammar or language bore, it's just easier for folks to read if it's laid out better?

---

### Post by devils_casper on 2006-10-01
[QUOTE=bigken]you must be doing something sadly wrong my son [/QUOTE]

Hi !

check [**this thread**]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/71830-how-install-windows-back-onto-fedora-machine.html") ! post # 5. a bit busy right now, couldn't find more.... if you need, i will search for you.




casper

---

### Post by bigken on 2006-10-01
> **devils_casper said:**
> Hi !

check [**this thread**]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/71830-how-install-windows-back-onto-fedora-machine.html") ! post # 5. a bit busy right now, couldn't find more.... if you need, i will search for you.




casper

well I have never had any problems repairing mbr in windows xp using ubuntu suse freespire and 1 or 2 other linux distros I have tried on 2 differnt boxes and 3 diffrent laptops ;)

---

### Post by bulldog on 2006-10-01
well I have never had any problems repairing mbr in windows xp using ubuntu suse freespire and 1 or 2 other linux distros I have tried on 2 differnt boxes and 3 diffrent laptops


Me neither,but maybe we are special :rolleyes:

---

### Post by devils_casper on 2006-10-01
[QUOTE=bigken]well I have never had any problems repairing mbr in windows xp using ubuntu suse freespire and 1 or 2 other linux distros I have tried on 2 differnt boxes and 3 diffrent laptops[/QUOTE]

i am in Linux world for last seven years and worked on several distros, several machines.... Partition Magic and XP CD creates a lot of problems in issues like this. i must say, you are very lucky !



casper

---

### Post by bulldog on 2006-10-01
> **devils_casper said:**
> i am in Linux world for last seven years and worked on several distros, several machines.... Partition Magic and XP CD creates a lot of problems in issues like this. i must say, you are very lucky !



casper

I like to think I'm very skilled,but then again.............maybe it **was** just luck.......;)

---

### Post by bigken on 2006-10-01
> **devils_casper said:**
> i am in Linux world for last seven years and worked on several distros, several machines.... Partition Magic and XP CD creates a lot of problems in issues like this. i must say, you are very lucky !



casper


I dont want to sound rude or anything but if thats the case why the hell do you use it ?

---

### Post by devils_casper on 2006-10-01
used Partition Magic a long time ago. now i dont use it and if you read my post correctly...i didn't recommend PM. i came across a lot of users having problems with PM. so... i never recommend it.




casper

---

### Post by bigken on 2006-10-01
> **devils_casper said:**
> used Partition Magic a long time ago. now i dont use it and if you read my post correctly...i didn't recommend PM. i came across a lot of users having problems with PM. so... i never recommend it.




casper

Ok m8 no probs 8)

---

### Post by bulldog on 2006-10-01
This will not help TS at all I'm afraid.

But the first car they made wasn't of the same quality as they made to day,want to say I'm familiar with PM8.0 if I'm not mistaken and used it a lot with NTFS format and can't say I have troubles with it.

Also used the Windows cd a variety of times and no complains from me................but I heard it was just luck:D :D

---

### Post by devils_casper on 2006-10-01
dont know how to delete. couldn't find delete option in EDIT POST. ](*,) 




casper

---

### Post by devils_casper on 2006-10-01
[QUOTE=ubu-jazzguy]One partition is win 32 and the other ubuntu. If i just wipe the ubuntu partition is this going to screw up booting to the other to win partitions??

should I back up my win partitions first? I have the 32 bit ubuntu downloaded and want to install it to the partition i have the 64 bit ubuntu on right now.

the 3rd hdd is just for storing movies and music etc. nothing booting off of it. Thanks a Lot.[/QUOTE]

nothing will go wrong ! boot up windows, type "diskmgmt.msc" in RUN dialog box of START button and delete Ubuntu partitions. 
on boot up, you will get grub> prompt. now boot up through Windows CD, select 'Repair(R)' and type 'FIXMBR'

windows fixed.... install Ubuntu 32 bit...




casper

---

