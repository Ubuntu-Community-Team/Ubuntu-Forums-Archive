---
title: "[SOLVED] You'll Love This How to safely Delete windows from a dual boot system."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-11-13
I have a dual boot system but need assistance to SAFELY get rid of everything windows. Windows doesn't boot anymore and I don't want it.

My System
Asus KNE 8 Deluxe
1024 ddr (updating soon)
3 physical boxed drives
i) IDE 320gb Parta) XP Pro Install Partb) unused Part c) NTFS Programs for win
ii) Sata 120gb NTFS (I think this is the place xp placed its bootloader?)
iii)Sata 120gb NTFS

Nvidia fx 5700 256mb
Dell 17"LCD
Diamond View 19" CRT

USB Drive Lacie 1Tb
USB Drive Samsung 120gb 

NOTE that confuses and scares me.
When I installed windows xp pro it insisted in formatting the SATA Drive ii) (this was the original drive before I added the IDE. It constantly referred to this as only windows could as the C: drive it then went on and fomatted and installed windows on Partition e: which is the first partition on the IDE. 
My fear is the boot loader is associated with both the sata and the IDE drive
the sata drive certainly has 11.2gb of data (? all windows dv19f folder, Recycler folder, System Volume inf. folder, autoexec.bat,file  boot.ini,file  Boot.bkk,file  config.sys,file IO sys file, MSDOD .sys file, NTDETECT.com file, ntldr file
Confused I am

Q. if I delete the windows partitions on the IDE part a and part c any problems????

Q. what do I do with the crap on the 1st sata....how do I amend the boot loader of Ubuntu and how do I back up my home.

Hopefully yours


Nigel

---

### Post by matthewcraig on 2007-11-13
"I have a dual boot system but need assistance to SAFELY get rid of everything windows. Windows doesn't boot anymore and I don't want it."

Does this statement contradicts itself?  Do you want to save the data or destroy it?
Also, it is not clear on your questions: What do you mean, "delete the windows ... any problems????"

It is not clear what you are intending to do.  Can you distill it down a bit?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
can you copy and past the out put of 
```
fdisk -l
```
here

and you just wanna delete windows and dont need any data from there
do you only have windows installed

---

### Post by mc4man on 2007-11-13
> Windows doesn't boot anymore and I don't want it.
As described your system isn't very linux "friendly" with all those ntfs partitions. I think I'd just backup any data, configs., whatever to an external device and start fresh. Your sata0 would be the best place for the Os (ubuntu ?). The sata1 would work nicely as an extended partition, you can add  logical drives as needed in whatever fs you want, and is good for cross drive work. The ide drive to suit your needs.

---

### Post by hogwartsnigel on 2007-11-13
Thanks guys,
I know I got confused writing it all.
Ihave a very good XP Pro installation that is on the system but doesn't load from boot...all the files are there though. I have backed up all I need from it so I can happily delete everything to do with windows.

I am keen to keep Ubuntu as it is as I maintain it for 4 user. so to simplify my question
How do I delete everything to do with windows so I am only running Ubuntu without having to re-install Ubuntu and start from scratch.
"I have a dual boot system but need assistance to SAFELY get rid of everything windows. Windows doesn't boot anymore and I don't want it."

[COLOR="DarkSlateGray"][I][COLOR="LightBlue"]Does this statement contradicts itself? Do you want to save the data or destroy it?
Also, it is not clear on your questions: What do you mean, "delete the windows ... any problems????"

It is not clear what you are intending to do[/COLOR][/I][/COLOR]


Just safely COMPLETELY REMOVE EVERYTHING TO DO WITH WINDOWS without effecting my existing UBUNTU.

The fdik -l gave me 

[COLOR="DarkSlateGray"][I]Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x045a7c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14596   117242338+  83  Linux

Disk /dev/sdd: 1004.0 GB, 1004000772608 bytes
255 heads, 63 sectors/track, 122062 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094df4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2      122062   980454982+   f  W95 Ext'd (LBA)
/dev/sdd5               2      122062   980454951    7  HPFS/NTFS
[/I][/COLOR]

Hope that helps

[COLOR="DarkSlateGray"]*As described your system isn't very linux "friendly" with all those ntfs partitions. I think I'd just backup any data, configs., whatever to an external device and start fresh. Your sata0 would be the best place for the Os (ubuntu ?). The sata1 would work nicely as an extended partition, you can add logical drives as needed in whatever fs you want, and is good for cross drive work. The ide drive to suit your needs*[/COLOR]

[COLOR="Black"]*Yes I know and once the drives are cleared for me I'll reformat and delet partitions...I guess that is the problems of trying to edge bets.*[/COLOR]

thanks for the help guys

I found somewhere a method of creating a back up of home unfortunately I need to find all that again.

Ta

---

### Post by CatKiller on 2007-11-13
You can delete those partitions with GPartEd. The two possible problem cases I can see are making sure you select the right partition to boot from, and if those partitions get automatically mounted.

The file to get right for the boot process is **/boot/grub/menu.lst**. There is a bunch of information on how to edit this file to **add** windows to it. You'll probably be able to work out the numbering from there. If it all goes wrong and the computer doesn't boot, you can still edit this file from the live cd, so don't be afraid of a little experimentation.

The file to check in case the partitions get automatically mounted is **/etc/fstab**. Just make sure that there aren't any references to the partitions you're going to delete and you should be fine.

Good luck!

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
> **CatKiller said:**
> You can delete those partitions with GPartEd. The two possible problem cases I can see are making sure you select the right partition to boot from, and if those partitions get automatically mounted.

The file to get right for the boot process is **/boot/grub/menu.lst**. There is a bunch of information on how to edit this file to **add** windows to it. You'll probably be able to work out the numbering from there. If it all goes wrong and the computer doesn't boot, you can still edit this file from the live cd, so don't be afraid of a little experimentation.

The file to check in case the partitions get automatically mounted is **/etc/fstab**. Just make sure that there aren't any references to the partitions you're going to delete and you should be fine.

Good luck!

your to confusing and i know what your talking about

so I would install gparted
```
sudo apt-get install gparted
```

then run gparted
```
gksudo gparted
```

then from here you can do what ever you need gparted is a great program i dont know why its not suggested as soon as some one says partition

if you cant figure out gparted ask and some (me probably )will walk you through it

---

### Post by hogwartsnigel on 2007-11-13
Thanks  Catkiller...wish me luck

I found that other thread about backing up home on a sep. partition here

 

Thanks again

Nigel

---

### Post by hogwartsnigel on 2007-11-13
Thanks Joe,
gee these forums are the best..you always feel supported

Nigel

I'll post how I get on later:)

---

### Post by hogwartsnigel on 2007-11-14
Hi guys, all went well. I used the live cd to edit my partitions and as such I know have a 320gb ide drive with a 30gb unformatted partition incase I want to install a secondary linux or whatever.My Ubuntu single partition a swap partition and two ext 3 parttions.
My other two installed drives are newly formatted to ex3 single partition.(1 I will use for back ups and the other as a depositary for a download collection (something I've done from old.

ANOTHER Q. Best back up utility so that when I do another fresh install my home files and settings can be transferred.??

Thanks

Nigel
Now with way too much memory 320gb +120gb+120gb +120gb+1Tb on this system

---

### Post by jaybombalous on 2007-11-14
I find it hard that anyone can use that much hd space. I have one 80g HD and have never filled it. 

Guess I just don't have a box full of copyrighted material. :(

---

### Post by CatKiller on 2007-11-14
Glad it went well.

> **hogwartsnigel said:**
> ANOTHER Q. Best back up utility so that when I do another fresh install my home files and settings can be transferred.??

I haven't used any backup software yet (I know) but if you have your /home on a separate partition then when you do a fresh install, all of your settings will be picked up. It doesn't guard against spontaneous catastrophic hard drive failure though, so you should back up as well.

---

### Post by chiefbearclaw on 2007-11-14
> **jaybombalous said:**
> I find it hard that anyone can use that much hd space. I have one 80g HD and have never filled it. 

Guess I just don't have a box full of copyrighted material. :(

Well he mentioned the machine was for 4 users. Also anyone who dabbles in Film/Music production will tell you.. 1TB is easy to fill up. For 4 users on one machine 1TB seems comfortable. :grin:

---

### Post by hogwartsnigel on 2007-11-14
My first dissappointed message on a  Linux forum, based on a presumtive attitude.
Jay, not that it is really any of your business but..............
I have over 1500 legitimate cds in collection, I have several podcast subscriptions to a local radio station (TRIPLEJ strongly recommend a visit to any music lovers)
I am a graphic designer married to a photographer. A single wedding shoot can be upto 20GBs of data, I back up  (OWNED) x box games for my 3 (360gb xbox's).
Please don't presume, as for 80gb...good luck to you..I remember when I was told in my early days "this computer has a 4gb harddrive...you'll never fill that.

I am no angel but have always undertaking a self imposed ethical sway to my computer usage...this is another reason I love LINUX, you can have it all an be legit, make a donation and I will.

Offering an olive branch but not PRESUMING you'll take it.

Thanks for the support to those that have shown it.

Q best back up software for my home files..Ta.

Nigel

---

### Post by hogwartsnigel on 2007-11-14
Sorry I didn't read passt Jays comments...tut tut me. Thanks I am trying on a seperate thread to find away either with the live disc or not to move my home file and opt file to the two partitions on my ide drive.....the link went dead at present and I am waiting input from the guy there..
If any of you know how to do it without re-installing (wish I knew more when I installed Gutsy) then please feel free to educate this sinner.

Ta muchly

Nigel

---

### Post by bulldog on 2007-11-14
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

Something to read :)

This part could be come handy,

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by hogwartsnigel on 2007-11-14
Thanks Bulldog.
After following your 2nd link used the live cd and followed the directions.
GREAT I now have a seperate home directory!
That link is now bookmarked way cool.

Does it matter that the original home is retain in the original partition?

Anyway BIG THANKS

---

### Post by bulldog on 2007-11-14
Don't think it matters,so let it be,root needs a /home too :)

Have fun.

---

### Post by hogwartsnigel on 2007-11-14
:)LOL
Well I'm off to bed thanks Bulldog..
Thanks
Nigel

---

