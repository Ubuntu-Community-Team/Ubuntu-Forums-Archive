---
title: "proper usage"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Leafx on 2008-03-06
alright, i am a college student, and i have a simple question. which operating system would provide better / proper usage along with ease / mobility or be more undergrad ideal? (vista / this) what i do on my computers now: web, music, word/spreadsheet processing, basically just basics. i used to game heavily on windows but i don't do that anymore and i wanted to try a new OS and this seemed like a good try. i came around the time where i needed a reformat and it seemed like a good time to try a new OS

 i have the OS running fine and everything, but i just don't get it! im trying to learn linux and all the commands still and i know i am definitely willing to learn. coming into ubuntu i knew only about half my programs would run on linux, ok. i don't mind that because i can find replacement programs. 

installing the programs is my problem, im reading all these guides and when i seem to try it, it never works out. i can't even install my printer onto my laptop either cause its not linux compatible, so there goes getting my school work onto paper. also the wireless networking doesnt work with ubuntu / this laptop, there goes mobility.  i can't seem to do **** while im on linux really that i couldnt do on vista, so should i just reconsider and reinstall windows?? as much fun as linux seems to be i dont see how its going to be better for me right now

---

### Post by Rocket2DMn on 2008-03-06
I suggest dual booting with Vista and Ubuntu if you're still interested in linux.  Being at school means you have to work with other people, most of who will have windows machines or apples with MS Office, and your school may provide you with software that will run only on windows or on an apple.  This means you can have with and learn with linux, but still be able to work through vista when needed.  Your school is unlikely to provide support for your system with linux as well, so if you have problems with their network or something, they can only help you if you are booted into windows.

If you start some new threads for your problems (one thread for each, please don't pile them all in one or you're less likely to get good help), people will help you troubleshoot them.  Printing and wireless can be tough sometimes, but 95% of the time we get it to work.

If you're like me, you may find that you can never fully escape windows because of software and professional dependencies in it, but it doesn't mean we can't make the most of linux, too.

---

### Post by Ardrias on 2008-03-06
If it's just a matter of needing a few Office programs or what not in Windows, I'd go with a Linux host and a Windows virtual machine if needed... I like to keep the virus quarantined... ;)

---

### Post by Leafx on 2008-03-06
dual booting sounds like a good idea, thanks
would it be a good idea to reinstall vista first?
i think i screwed up my partitions anyways, when i go to computer, properties on file systems i only have 3 gigs total for some reason, 2.something used on the OS install. im supposed have 80gb and there are no other drives showing.
what i love about linux is the security and virus / other features that i dont have to deal with as compared to windows. i definitely do want to give linux a go

---

### Post by Rocket2DMn on 2008-03-06
When setting up a dual boot, it is easiest to layout your partitions first, starting with installing Windows.  So only give windows as much as you want and leave the rest of the drive as empty space.  After installing windows, install Ubuntu so it will install GRUB and detect vista automatically, so now GRUB reinstallation and manual adding of vista is needed.
You don't have to remove linux, you can just resize your partition from the LiveCD or GParted LiveCD to open up space for windows, but you will have to reinstall GRUB and add vista after you do the windows install.
If you decide to keep your current linux setup, let me know and I'll walk you through the steps of getting the drive setup, then reinstalling GRUB and adding windows to it.

However, if you think you want to just start fresh, it's much easier :)

---

### Post by Arthur Archnix on 2008-03-06
I found the best way to learn was just to get rid of Windows. Otherwise when I frustrated with something I'd just boot back into windows. 

That being said, I do have XP on virtual box for my spss work and office 2003 when I edit friends papers and submit my own, I like to scan them over in word before sending them to confirm that openoffice did it properly.

I think your wireless will be a snap, but printers will be very hit and miss. If I need to print I put it on a flash drive and print. On the plus side, it means I've removed almost all cups and foo related stuff from my lappy, making it a touch more snappy.

Dual-booting is certainly the safer smarter way to go.

Last thing. If you decide to go for linux hard-core, here's what I'd suggest, get yourself a gparted live cd and create a partition layout similar to the following
> 1 GB partition called swap (primary partition)
The rest of the disk extended partition.
6GB ext3 partition
6GB ext3 partition
4GB ext2 partition
60GB ext3 partitionThe 6GB partitions are for you linux installs. You'll want one for ubuntu... then maybe you hear something good about mint and you want to try it out, but you don't want to have to reinstall ubuntu. So you put Mint on the second one and dual boot. Maybe you like it better, but then ubuntu Hardy is released and you want to check it out again, so you install that on the first partition. Plus, if and when you do mess up your system, rather than booting a live cd to fix it you just boot into your other linux system and fix it there. No downtime. 
The 4GB is a place to backup your install of your favorite system. So let's say you've got ubuntu on partition one, and your experimenting with hardy on partition two, and you have a backup of ubuntu on the 3rd partition. If and when you break it beyond repair, you just boot into the second system, type one command into the terminal and it restores your system. Simple.

The last partition is your data. Music, movies, files, etc. It's not tied down to one system so you can reinstall and mess up and not worry about backing up your data quite as much. Still important though, but only as a general rule of thumb. If you were going to reinstall and had all your data in /home then you'd have to be a little more careful. I've got my data on its own partition and I just make symlinks into my home directory. Symlinks are a bit like shortcuts in windows, but more powerful. For example, I don't want to have to retrain exaile what my favorite albums are every time I install. And I want changes to song ratings made on one system (ubuntu) readable on the other system (currently xubuntu), so I move the exaile folder to my data partition, which is shared between systems, then just create symlinks to it where exaile thinks it ought to be (i.e, ~/.exaile). I do the same (or similar) for dictionaries in openoffice, thunderbird profiles, firefox profiles and my sunbird calender. 

Phew.... this coffee really hit me

---

### Post by Paqman on 2008-03-06
> **Leafx said:**
>  i can't even install my printer onto my laptop either cause its not linux compatible, so there goes getting my school work onto paper. also the wireless networking doesnt work with ubuntu / this laptop, there goes mobility.  i can't seem to do **** 

First of all, don't despair. Neither of these problems are due to any shortcomings on your part. Hardware compatibility is _the_ biggest problem for Linux. A lot of manufacturers don't support Linux, because not enough people use it. Wifi and printers seem to be the two most common culprits for this.

The good news is that many, many people have the exact same problems. This forum has vast amounts of information available on getting wifi and printers to work, and many very clued-up people who will be happy to help.

I'd suggest you go for the dual boot for now while you get your hardware snags sorted. Check out [Psychocats](http://www.psychocats.net/ubuntu/) for lots of good info on how to do this. Partitioning for dual-boot on an 80GB drive i'd go for something like: 
10GB EXT3 for Linux root (/), 
1-2GB swap, 
30-50GB NTFS for Windows, depending on how much software you want to install.
and the rest as a /home partition (optional, but very handy). 

You can only have 4 primary partitions normally, so you might want put some/all of those inside an extended partition like Arthur Archnix says. That'll let you dodge the 4 partitions rule if you suddenly decide you need another partition, and is actually pretty straightforward.

Alternatively you can just ask to Ubuntu installer to create it's own partitions like Rocket2DMn suggested. That'll create a perfectly good partitioning setup in one click. If you want anything fancy you can always reinstall later.

---

### Post by Baelari on 2008-03-06
> Last thing. If you decide to go for linux hard-core, here's what I'd suggest, get yourself a gparted live cd and create a partition layout similar to the following
Quote:
1 GB partition called swap (primary partition)
The rest of the disk extended partition.
6GB ext3 partition
6GB ext3 partition
4GB ext2 partition
60GB ext3 partition
The 6GB partitions are for you linux installs. You'll want one for ubuntu... then maybe you hear something good about mint and you want to try it out, but you don't want to have to reinstall ubuntu. So you put Mint on the second one and dual boot. Maybe you like it better, but then ubuntu Hardy is released and you want to check it out again, so you install that on the first partition. **[B]Plus, if and when you do mess up your system, rather than booting a live cd to fix it you just boot into your other linux system and fix it there. No downtime.**
The 4GB is a place to backup your install of your favorite system. So let's say you've got ubuntu on partition one, and your experimenting with hardy on partition two, and you have a backup of ubuntu on the 3rd partition. If and when you break it beyond repair, you just boot into the second system, type one command into the terminal and it restores your system. Simple.[/B]

The last partition is your data. Music, movies, files, etc. It's not tied down to one system so you can reinstall and mess up and not worry about backing up your data quite as much. Still important though, but only as a general rule of thumb. If you were going to reinstall and had all your data in /home then you'd have to be a little more careful. I've got my data on its own partition and I just make symlinks into my home directory. Symlinks are a bit like shortcuts in windows, but more powerful. 


This is *exactly* what I'm looking to do, I think, but have a backup of each OS, including lolVista (I Have an NTFS external for media, etc...). I mess up my systems beyond repair pretty often, and reinstall just as often. I'd like to save a backup of a fresh install after I get all my preferred programs working for each OS, so I don't have to reinstall them the long way, every time I poke at a system file. 

Why is the backup ext2 instead of 3? and would I need a separate partition for each OS's backup? What would I need to do for a Windows backup? Would the backup restore every OS on the computer, or preferably,  just the one I FUBARed?

Also, I need to work around the necessity of a live CD. The laptop I just ordered will not have an optical drive.

---

### Post by Arthur Archnix on 2008-03-06
> You can only have 4 primary partitions normally, so you might want put some/all of those inside an extended partition like Arthur Archnix says. That'll let you dodge the 4 partitions rule if you suddenly decide you need another partition, and is actually pretty straightforward.

Well, the layout I gave was for linux only, but Windows can't use an extended partition to boot from. So it would have to be more like
> Primary partition for Windows
Extended partition for everything else.

And to Baelari

> Why is the backup ext2 instead of 3? and would I need a separate partition for each OS's backup? What would I need to do for a Windows backup? Would the backup restore every OS on the computer, or preferably, just the one I FUBARed?

I fear going off-topic or threadjacking here, so if you want more and better answers it might be best to open up a new thread on the subject. Briefly, (1) ext2 is faster and your not using the backup partition much so no need for journalling. (2) No. Just separate folders in the partition and enough space for the backups. (3) The same as linux (man dd) (4) Either (man dd) or check out the forums.

---

### Post by Paqman on 2008-03-06
> **Arthur Archnix said:**
> Windows can't use an extended partition to boot from


You learn a new thing ever day. Cheers!

---

