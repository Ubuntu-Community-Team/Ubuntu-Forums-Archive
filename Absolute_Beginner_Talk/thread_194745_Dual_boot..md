---
title: "Dual boot."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-06-11
I want to dual boot. I have a windows os that I dont want to loose. I was going to just partition using the ubuntu boot partition, but dell has packed 4 partitions onto my disk. All for windows. And it says I can only use 4. So what can I do?
EDIT: I also want to have a FAT32 partition for my music, that way I can share it between windows and linux. Sound like a plan?

---

### Post by baldwinny on 2006-06-11
All partitions for Windows? Is one of them that hidden partition for Dell's factory system recovery? If so that's generally useless and worth deleting.

---

### Post by Jason_25 on 2006-06-11
You can use [this]("http://www.fs-driver.org/") and access your ext3 partitions from windows.  Fat32 isn't as error proof and has a 4 GB individual file size limit.

---

### Post by catlett on 2006-06-11
What you need to do is advanced. Do you have experience with partitioning? Do you have an application already that can copy the data of a partition to a dvd disk or external drive and then back to the hard drive again?
These are the things you need to do. You need to take the data off one of the partitions and store it somewhere. Then you will have to delete that partition. Next you will have to make that partition an extended partition. Inside the extended partition you will have to make 4 partitions, 1 ntfs or fat32 to hold the data you just removed. A swap partition to be used as swap by linux. An ext3 partition for the linux install. And a fat32 for your music partition.
The 1st has to be large enough to hold the data removed. The swap has to be 500mb, at least. The ext3 for linux should be at least 7gb. The rest can go to your music file.
A good open source program to copy data is "partimage", google it and you wil find the web site. A good open source partitioner is  "gparted live", again google it and you will find the web site.

If you want my advice, go to your local computer shop and buy a pulled (used, means pulled from an old working computer) 10-15gb hard drive. Install it in a spare bay in your computer. When you install choose that drive and let the installer use the entire drtive for linux.
Just use one of your 4 partitions as a "transfer" between linux and windows.

There are links in my signature to 2 good how tos on installation. One shows the text base install and the other shows the install from the live cd.

> baldwinny  	All partitions for Windows? Is one of them that hidden partition for Dell's factory system recovery? If so that's generally useless and worth deleting. It's only worthless if you don't plan on recovering your installation. That partition holds a copy of your original install. If something happened to your system you can choose the option at start up to recover. What happens then is your computer boots to that partition and a recovery program runs that transfers the copy of your installation from the partition back to your main partition. I would not delete that AT ALL. If something goes wrong with your ubuntu install, you can use that partition to get your windows back up abd running.

---

### Post by jason.b.c on 2006-06-11
[QUOTE=baldwinny]All partitions for Windows? Is one of them that hidden partition for Dell's factory system recovery? If so that's generally useless and worth deleting.[/QUOTE]

Generally useless..?? =; 

Why would you tell him that..???   I mean, If push comes to shove and he ever needs to restore windows then how's he supposed to do that if the restore partition is gone..?? :-&

---

### Post by Jason_25 on 2006-06-11
[QUOTE=jason.b.c]Generally useless..?? =; 

Why would you tell him that..???   I mean, If push comes to shove and he ever needs to restore windows then how's he supposed to do that if the restore partition is gone..?? :-&[/QUOTE]
The install CD like everyone else that uses windows?

---

### Post by catlett on 2006-06-11
[QUOTE=Jason_25]The install CD like everyone else that uses windows?[/QUOTE]
The windows install cd is not even close to the  Dell system that came with his computer.  A windows install cd just gives you the base system. It does not have all the propriety drivers and software that Dell includes in their software package. 
DO NOT erase your recovery partition. It has your FULL Dell system that was there when you bought your computer.  i.e.  If you got Office it is there but not on a windows install disk. If you got Nero it is there and not on a windows disk. The drivers that run your system are there. If you use the windows install cd you take a chance that XP can find the correct drivers online or you have to go website to website hunting.

Trust me go to the local store or ebay and get a used 15 gb hard drive and use that for ubuntu. It is very easy to install and it will make your install of Ubuntu  very easy as well. I haven't seen a Dell without at least one free bay, use it and you won't have any worries about which partition to use.

---

### Post by jason.b.c on 2006-06-11
[QUOTE=Jason_25]The install CD like everyone else that uses windows?[/QUOTE]

So i assume that you got one (**Free**) with your new computer from the store.?

Last time i checked, When purchasing a new computer, Windows is already installed from the factory and you have to purchase the windows disk seperately if you want one to go with your new computer..

> The windows install cd is not even close to the Dell system that came with his computer. A windows install cd just gives you the base system. It does not have all the propriety drivers and software that Dell includes in their software package.
DO NOT erase your recovery partition. It has your FULL Dell system that was there when you bought your computer. i.e. If you got Office it is there but not on a windows install disk. If you got Nero it is there and not on a windows disk. The drivers that run your system are there. If you use the windows install cd you take a chance that XP can find the correct drivers online or you have to go website to website hunting.

Thats right..;)

---

### Post by jimrz on 2006-06-11
[QUOTE=fuzzyhair]I want to dual boot. I have a windows os that I dont want to loose. I was going to just partition using the ubuntu boot partition, but dell has packed 4 partitions onto my disk. All for windows. And it says I can only use 4. So what can I do?
EDIT: I also want to have a FAT32 partition for my music, that way I can share it between windows and linux. Sound like a plan?[/QUOTE]

Surely one of your partitions is an "extended" partition,which may also have another "logical" partition in it. Your win + dell recovery are surely both "primary" partitions. Generally, you can have up to 4 partitions on 1 hd. One of these can be an "extended" partition which can contain many "logical" partitions, which do NOT count against your total of 4 allowed.

It would be helpful if you could post your partition table here. Then we could see specifically what you have to work with.

---

### Post by Jason_25 on 2006-06-11
[QUOTE=jason.b.c]So i assume that you got one (**Free**) with your new computer from the store.?

Last time i checked, When purchasing a new computer, Windows is already installed from the factory and you have to purchase the windows disk seperately if you want one to go with your new computer..



Thats right..;)[/QUOTE]
If you weren't supplied one when you bought it (problem number one IMO) The manufacturer is required to give you the original windows disk, since you own the license for the copy of windows.

---

### Post by jason.b.c on 2006-06-11
[QUOTE=Jason_25]If you weren't supplied one when you bought it (problem number one IMO) The manufacturer is required to give you the original windows disk, since you own the license for the copy of windows.[/QUOTE]

No there not required to give you one.!  Only if you purchase it seperately..

Trust me, I've been all through this one with the people/salesmen at **BestBuy**..And also with the friendly people at **HP**, Wich i spoke with for almost an hour..  I was told that straight up..

They won't just *give you one* and then they don't make a profit on it..:lol:

---

### Post by RRS on 2006-06-11
[QUOTE=jason.b.c]No there not required to give you one.!  Only if you purchase it seperately..

Trust me, I've been all through this one with the people/salesmen at **BestBuy**..And also with the friendly people at **HP**, Wich i spoke with for almost an hour..  I was told that straight up..

They won't just *give you one* and then they don't make a profit on it..:lol:[/QUOTE]

Same with Dell, and probably a couple others.

Also most that do provide a cd give you a propriatory "system restore" disc especially for that machine and often doesn't include some of the repair tools included on the windows disc that you would buy seperately for a computer with no os.

---

### Post by confused57 on 2006-06-11
[QUOTE=fuzzyhair]I want to dual boot. I have a windows os that I dont want to loose. I was going to just partition using the ubuntu boot partition, but dell has packed 4 partitions onto my disk. All for windows. And it says I can only use 4. So what can I do?
EDIT: I also want to have a FAT32 partition for my music, that way I can share it between windows and linux. Sound like a plan?[/QUOTE]

If you purchased your Dell new, did it come with a CD?  Is it labelled "Recovery" CD" or "Operating System", which I think is the Windows full-installation CD?
I have a Dell Dimension 4550, which came with the latter CD and the instructions in the handbook lead me to believe it's the full Windows install. Partition#1 on my system is a 35mb Dell utility, partition#2 is Windows, no other partitions...leads me to believe your other partitions are for recovery Windows install.

---

### Post by jason.b.c on 2006-06-12
[ What if i don't have the disk.?]("http://ask-leo.com/i_dont_have_an_installation_cd_for_windows_xp_what_if_i_need_one.html")

[Where's my money..??]("http://blogs.sun.com/roller/page/swinger/20051205")

---

### Post by confused57 on 2006-06-12
Hope this isn't too off-topic to this thread; but I have question about installing Windows. If I have another WindowsXP installation CD, other than the CD that was used to install XP on particular pc, could I use any XP install CD to install, but enter the XP license# from the label on the computer I'm installing XP to?  If this makes any sense...

Therefore, I could install using another XP CD, but just enter the license# for the computer installing onto.

---

### Post by aysiu on 2006-06-12
I think each Windows XP CD has its own activation code. Someone can correct me if I'm wrong about this.

---

### Post by elemental666 on 2006-06-12
I could be mistaken, but I think the code and the XP distro type match up.

Meaning if you have an XP Pro retail cd you need a retail code, if you have an OEM cd you need an OEM code, Licence Volume codes will work with any distro I believe...

none of this gaurantees passing the genuine advantage crap though...

---

### Post by brentroos on 2006-06-12
*

---

### Post by Jason_25 on 2006-06-12
[QUOTE=jason.b.c]No there not required to give you one.!  Only if you purchase it seperately..

Trust me, I've been all through this one with the people/salesmen at **BestBuy**..And also with the friendly people at **HP**, Wich i spoke with for almost an hour..  I was told that straight up..

They won't just *give you one* and then they don't make a profit on it..:lol:[/QUOTE]
**Wrong.**

Acccording to [this]("http://forums.us.dell.com/supportforums/board/message?board.id=sw_winxp&message.id=126299&query.id=26698#M126299") thread and others on the dell forums, the recovery partition only contains an image of a "dell reinstall" and upon customer request, they will ship the xp system cd at little or no charge.  They just don't ship the disks anymore to save themselves cost.  For all the dell noobs out there that when their xp gets ridden with viruses, they just buy a new computer.

---

### Post by jason.b.c on 2006-06-12
[QUOTE=aysiu]I think each Windows XP CD has its own activation code. Someone can correct me if I'm wrong about this.[/QUOTE]


Yea, But that hasn't stopped people before..=; 

From what i was told ( or i should say, *To the best of my knowlage* ) You **"can"** do that, So long as that particular install cd was activated **at least** 60 days ( two months ) ago.

The reason why you can do that is the microsoft activation servers have a hard time telling the differance  between what computer is what, The thing is, Your only allowed to reformatte your hard drive and reinstall windows so many times within a certain time period.( *like i said, two or three months* ). So yea, That should be ok so long as you've had the other windows of the same disk installed and running for a while.

I don't really think anything will come of it..:rolleyes:

---

### Post by M@dMerC on 2006-06-12
Any computer seller that supplies a windows installation on the computer that is purchased is required to supply a copy of windows on disk to that customer (usually an OEM version) and as far as the original problem i agree that your best and easiest course of action would be to obtain another harddrive to install linux on this makes everything easy and the only thing you really need to worry about then is making sure windows is installed first which it seems to be

---

