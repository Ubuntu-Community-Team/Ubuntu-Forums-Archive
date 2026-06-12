---
title: "Few Questions"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by kc0eak on 2006-05-03
I have decided that I'd like to install Ubuntu on my hard drive, but I have a few questions before diving into the install.

- When I get to the install, I am going to format the hard drive and re-install Windows, then dual-boot my computer.  When I do this, I am going to do some major partition work.  I'll skip what partitions I'm going to create for Windows, but I have some questions about the Linux partitions.
     - Is it possible to install Ubuntu to one partition, use another partition for the swap file, another partition to install applications to, and another partition for my home directory?
     - If this is possible, what is the optimal size for the swap file partition?
     - Also if this is possible, will I just need to move the home directory and the directory for applications from one partition to another, or will I need to do something special during the install to get those directories into their own partition?
     - How big should the partition for Ubuntu itself be, not counting space I'll need for my personal files and application files?

- I have a large number of files that were created in the NTFS file system.  I know that Linux does not natively support NTFS write, but I have seen some applications that allow writing to NTFS.  Are these applications stable, and if so, does anyone have any recommendations as to which one I should be using?

- How long does the average Ubuntu install take?  This isn't critical to know, it's just that with my schedule, I won't be near my home for some time this summer, and when I install Ubuntu, I'd like to be near another computer for internet access in case I have any problems.

- Finally, I have seen some online guides to help with the transition from Windows to Ubuntu.  Does anyone have any suggestions about some guides to ease the transition?

Thank you very much in advance.  I am very excited to be switching to Linux and appreciate all help with the transition.

---

### Post by ComplexNumber on 2006-05-03
> Is it possible to install Ubuntu to one partition, use another partition for the swap file, another partition to install applications to, and another partition for my home directory? >       - If this is possible, what is the optimal size for the swap file partition? you only really need 3 partitions:
-root (/). this is where everything goes
-home directory. this is where your home directory is stored. this is useful because you can do a fresh install from disk yet still keep all your settings intact. it also allows you to put odds'n'ends that you want to keep inbetween fresh installations. if you don't set aside the /home directory in its own partiton, your home directory is stored in the '/' partition.
-swap partition. make this to be approx twice the size of your RAM.

some people have a /boot partion too, but i don't know what advantage there is to most. the boot sector is perhaps best stored on the MBR.

> 
- Also if this is possible, will I just need to move the home directory and the directory for applications from one partition to another, or will I need to do something special during the install to get those directories into their own partition? i'm not entirely certain what you mean exactly. just partition them as above.



> - How big should the partition for Ubuntu itself be, not counting space I'll need for my personal files and application files? its not divided up like that. like i say, just partition as above. have at least 3GB for the '/' partition. about 1GB or 2GB for your /home partition. how much harddrive can you set aside for ubuntu? then i can give your a rough estimate of how much space you could use for each.


> - I have a large number of files that were created in the NTFS file system. I know that Linux does not natively support NTFS write, but I have seen some applications that allow writing to NTFS. Are these applications stable, and if so, does anyone have any recommendations as to which one I should be using? i honestly don't know about this just yet.

> 
- How long does the average Ubuntu install take? This isn't critical to know, it's just that with my schedule, I won't be near my home for some time this summer, and when I install Ubuntu, I'd like to be near another computer for internet access in case I have any problems. depends upon how fast your processor is and how much RAM you have.

> 
- Finally, I have seen some online guides to help with the transition from Windows to Ubuntu. Does anyone have any suggestions about some guides to ease the transition? you may find [this]("http://www.linuxnewbieguide.org/") useful.

---

### Post by nalmeth on 2006-05-04
ComplexNumber seems to have answered most of your questions.
Your swap should be at least the same size as your RAM.
NTFS writing is not considered stable yet, you will risk data loss.
Safest thing to do would be to create a fat32 data partition to move your files you need from windows, and you can store your linux docs/media there too.
Oh, and pick up automatix to get everything you'll probably need up and running.

---

### Post by ComplexNumber on 2006-05-04
>  Your swap should be at least the same size as your RAM. i thought the general rule was that it had to be approx, or at least, twice the size of the amount of RAM. this is advice given to me since the very first issue of Linux Format magazine. other publications state this too. for example, red hat states [here]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/ch-swapspace.html"):
>     The size of your swap should be equal to twice your computer's physical     RAM for up to 2 GB of physical RAM. For physical RAM above 2 GB, the     size of your swap should be equal to the amount of physical RAM above 2     GB. The size of your swap should never less than 32 MB. i think part of the reasoning here is that, because memory is so cheap, the amount of memory is very often upgraded in a system, so its best to make allowances for this. also, i think it was perhaps only the older systems that needed twice as much, but its not so much necessary if the user has 512MB of RAM or more.

other reasoning is mentioned [here]("http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=218"):
>  So, how much do you assign to swap? Good question. In general, I still support the suggestion is twice as much as RAM. This is the "good reason" I mentioned for having more swap than physical RAM. Creating a large swap space is easier to do it now and waste the space than to reinstall later. Another good reason is when you have more than one user running graphical applications. In this case, then even setting swap to two times RAM is reasonable. If all the space is taken up on the primary hard disk, you can add a hard disk and use the swap command to add additional swap space.

---

### Post by kc0eak on 2006-05-04
I have a 60 GB hard drive, but I am still considering how I want to divide that up.  What I think I am going to do is give Windows XP Home about 5 GB, formatted as NTFS, use another partition for my Windows programs (the size of this will be 5-10 GB), also formatted as NTFS, then I'll put all of my files onto another partition, the size of which will be 10-20 GB, formatted as FAT32, going by the suggestion of nalmeth.  Just to be sure, this will allow Ubuntu to read my files, even though they were created in Windows, correct?

With those partitions set up, if I were to use the max. size I'm planning for those, that will give me a total of 35 GB used.  This would leave me with 25 GB left, which will be devoted to Ubuntu.  I have 512 MB of RAM, so I think I'll make the swap partition 1 GB in size.  Since my files will reside on the FAT32 partition, my home directory shouldn't have to be as large since I won't be storing many files there, so I think I'll make that about 5 GB in size, which would leave about 19 GB left for the root directory.  Some of this space will probably be put with the FAT32 partition so I have more space there, but these sizes are certain yet.

Any suggestions on how I should change this would be appreciated.

Then next thing is that I will be re-installing Windows XP Home from scratch, so I will be using that setup to do the partitioning.  Is there another program that would be easier to use, or should I just stick to the Windows setup?  The one thing with the program if there is another one that I should use is that it would have to be free.  I am currently on a very limited budget and can't afford to be purchasing a program that I'll just use this one time, and maybe not again for a long time.

Also, my processor is an Intel P4 w/ HT at 2.8 GHz, so if anyone has any idea as to how long it'll take to install, that would be nice to know.

I think that's all the questions I have for now.  As long as I find out for sure that Linux can read / write to a FAT32 partition that my Windows files are on, that'll be the biggest thing.  Thank you for all the help.  Linux seems like a great OS from what I can see.

---

### Post by Jeroen V on 2006-05-04
[QUOTE=kc0eak]Just to be sure, this will allow Ubuntu to read my files, even though they were created in Windows, correct?[/QUOTE]
Yes this is correct

[QUOTE=kc0eak]Is there another program that would be easier to use, or should I just stick to the Windows setup?[/QUOTE]
If you download the Dapper CD, you could use it's partition manager to manage all of your partitions and make some new ones. 
When you made these, I should install XP Home from the XP-cd, and when this is done, Install Ubuntu. Ubuntu sees that XP is installed, and automatically makes a nice dual-boot program, called GRUB, so that you can choose into which OS you want to work!


[QUOTE=kc0eak]Also, my processor is an Intel P4 w/ HT at 2.8 GHz, so if anyone has any idea as to how long it'll take to install, that would be nice to know.[/QUOTE] 
I'm guessing 10 minutes with the latest Ubuntu Dapper.

---

### Post by steve.horsley on 2006-05-04
I agree that you probably only need a / partition and a /home partition (and swap of course). The root partition should be 5-15 gig, depending on how much crap you want to install - UT2004 fills a lot. I suggest you also put in a spare partition for a second experimental / - then you can triple-boot and test your linux upgrades before jumping on with both feet.

Allow a couple of hours for the base install. If all goes well, half that.  It depends a lot on your PC, because there's a lot of I/O and a lot of decompression going on. You also need time to tinker with the partitioner.

---

### Post by nalmeth on 2006-05-04
>  thought the general rule was that it had to be approx, or at least, twice the size of the amount of RAM.
This is true, it is commonly recommended, but I've never seen more than half of my swap being used up, infact, even when my RAM is all used up, the swap is rarely used.
If I'm low on disc space, I don't want to waste another half gig that won't ever be used.
I think they recommend it being so high, because your harddrive can't work as fast as your RAM can, and having a lot to go around will help in super high strain operations.

Go with double if you have the space to spare, and want to play some hardcore games, but I doubt it will be used.

---

### Post by kc0eak on 2006-05-04
One additional question that has come to mind.  While installing Ubuntu, does it ask which partitions I would like to install the root, home and swap partitions to, or does it assume I want them all on the same partition unless I specify otherwise?

Thanks guys.

---

### Post by nalmeth on 2006-05-04
[quote=kc0eak]One additional question that has come to mind.  While installing Ubuntu, does it ask which partitions I would like to install the root, home and swap partitions to, or does it assume I want them all on the same partition unless I specify otherwise?

Thanks guys.[/quote]
It won't exactly ask you, but the default plan it gives is one partition for root and home, and a swap partition.
Unless you specify otherwise

---

### Post by Sef on 2006-05-04
> Windows XP Home about 5 GB

That would be ok if you rarely plan on using Windows.  If you were planning on using it a bit, then I would do closer to 10 GB.

---

### Post by kc0eak on 2006-05-04
[QUOTE=nalmeth]It won't exactly ask you, but the default plan it gives is one partition for root and home, and a swap partition.
Unless you specify otherwise[/QUOTE]
So, if it wants to put root and home on the same partition, how do I make it put each of them on a seperate one, as was suggested earlier in the post?

Also, just to be sure, it will allow me to select which partition I want to install each one to and not just pick one, correct?  I just want to be sure so that I don't end up putting the swap on the biggest partition or something dumb like that.

Thanks

---

### Post by ComplexNumber on 2006-05-04
[quote=nalmath]but I've never seen more than half of my swap being used up, infact, even when my RAM is all used up, the swap is rarely used.[/quote] i haven't on mine either. i have 384MB of RAM. the only time its gone quite high in terms of swap usage is when i'm compiling about 5 or more different tarballs in parallel, each in its own terminal.

> 
That would be ok if you rarely plan on using Windows.  If you were planning on using it a bit, then I would do closer to 10 GB i think thats more nearer the mark. when i did a clean install of windows, then put vs.net and office, i was using about 8-10GB (or thereabouts). windows has a habit of really filling up with junk and superfluous packages very very quickly. its easy to underestimate how much space is needed. i would recommend about 15-20GB. linux doesn't need that much. i have always struggled to fill up more than about 8GB. however, make further allowances for where you are going to be storing your library of media files (eg's videos and such like) because that will really eat up space.

> 
So, if it wants to put root and home on the same partition, how do I make it put each of them on a seperate one, as was suggested earlier in the post? i would put your /home directory in its own partition. also, it may be a useful to configure the partitions such that the '/' is at the end. this is so that you can add more space easily as and when required. also, set your swap areas inbetween windows and linux because that will give you some slight speed advantage. i think its because the nearer the swap is to the start of the disk, the faster it can access it.

partition your drive as follows:
**-'windows'** (windows _must_ be at the start. it won't work otherwise. i made the mistake of putting linux at the start, then had to uninsatll linux because windows wouldn't be placed anywhere other than the start) -** 10-20GB**
[B]-'swap' - (2 x RAM)
-'/home' - 5GB [/B](if you're going to be storing loads of videos and mp3's, make it about 10GB)
[B] -'/' - 10GB

[/B]> Also, just to be sure, it will allow me to select which partition I want to install each one to and not just pick one, correct? I just want to be sure so that I don't end up putting the swap on the biggest partition or something dumb like that. choose manual and custom partitioning (i can't remember the precise language used)

---

### Post by kc0eak on 2006-05-04
[QUOTE=ComplexNumber]i haven't on mine either. i have 384MB of RAM. the only time its gone quite high in terms of swap usage is when i'm compiling about 5 or more different tarballs in parallel, each in its own terminal.

 i think thats more nearer the mark. when i did a clean install of windows, then put vs.net and office, i was using about 8-10GB (or thereabouts). windows has a habit of really filling up with junk and superfluous packages very very quickly. its easy to underestimate how much space is needed. i would recommend about 15-20GB. linux doesn't need that much. i have always struggled to fill up more than about 8GB. however, make further allowances for where you are going to be storing your library of media files (eg's videos and such like) because that will really eat up space.

 i would put your /home directory in its own partition. also, it may be a useful to configure the partitions such that the '/' is at the end. this is so that you can add more space easily as and when required. also, set your swap areas inbetween windows and linux because that will give you some slight speed advantage. i think its because the nearer the swap is to the start of the disk, the faster it can access it.

partition your drive as follows:
**-'windows'** (windows _must_ be at the start. it won't work otherwise. i made the mistake of putting linux at the start, then had to uninsatll linux because windows wouldn't be placed anywhere other than the start) -** 10-20GB**
[B]-'swap' - (2 x RAM)
-'/home' - 5GB [/B](if you're going to be storing loads of videos and mp3's, make it about 10GB)
[B] -'/' - 10GB

[/B] choose manual and custom partitioning (i can't remember the precise language used)[/QUOTE]
I guess that really didn't answer my question.  Nalmeth said that it will, by default, put the root and home directories in the same partition.  I'd like to place them on seperate partitions, and nalmeth also said that this is possible, you just have to specify that's the way you want it.

My question is, how do you specify that you want them on different partitions?

Also, during the installation, do I get to select which partition to put the directories on, or does Ubuntu automatically select which ones to use?

Thanks again!

---

### Post by kc0eak on 2006-05-04
[QUOTE=ComplexNumber]i haven't on mine either. i have 384MB of RAM. the only time its gone quite high in terms of swap usage is when i'm compiling about 5 or more different tarballs in parallel, each in its own terminal.

 i think thats more nearer the mark. when i did a clean install of windows, then put vs.net and office, i was using about 8-10GB (or thereabouts). windows has a habit of really filling up with junk and superfluous packages very very quickly. its easy to underestimate how much space is needed. i would recommend about 15-20GB. linux doesn't need that much. i have always struggled to fill up more than about 8GB. however, make further allowances for where you are going to be storing your library of media files (eg's videos and such like) because that will really eat up space.

 i would put your /home directory in its own partition. also, it may be a useful to configure the partitions such that the '/' is at the end. this is so that you can add more space easily as and when required. also, set your swap areas inbetween windows and linux because that will give you some slight speed advantage. i think its because the nearer the swap is to the start of the disk, the faster it can access it.

partition your drive as follows:
**-'windows'** (windows _must_ be at the start. it won't work otherwise. i made the mistake of putting linux at the start, then had to uninsatll linux because windows wouldn't be placed anywhere other than the start) -** 10-20GB**
[B]-'swap' - (2 x RAM)
-'/home' - 5GB [/B](if you're going to be storing loads of videos and mp3's, make it about 10GB)
[B] -'/' - 10GB

[/B] choose manual and custom partitioning (i can't remember the precise language used)[/QUOTE]
I guess that really didn't answer my question.  Nalmeth said that it will, by default, put the root and home directories in the same partition.  I'd like to place them on seperate partitions, and nalmeth also said that this is possible, you just have to specify that's the way you want it.

My question is, how do you specify that you want them on different partitions?

Also, during the installation, do I get to select which partition to put the directories on, or does Ubuntu automatically select which ones to use?

Thanks again!

---

### Post by confused57 on 2006-05-04
Here's the definitive guide for /home on separate partition:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

I've used it for a separate home partition & works pretty well.  During the partition setup, I had to "go back" a couple of times until I got it right and you'll have a chance to see the final partitioning scheme before it actually sets up the partitions.

---

### Post by catlett on 2006-05-04
[QUOTE=kc0eak]One additional question that has come to mind.  While installing Ubuntu, does it ask which partitions I would like to install the root, home and swap partitions to, or does it assume I want them all on the same partition unless I specify otherwise?

Thanks guys.[/QUOTE]
You can do an easy default install and partition or you can get involved.
There are 2 easy ways.
1 is to choose resize your existing partition. This is used when your hard drive is formatted for 1 partition with windows on it. If you choose this the install will auto matically partition a swap partition and 1 other partition with root and home on it.
The other easy way is to already have a partition for ubuntu ready. When you get to the installer you can choose to "manually edit your partition table". When you choose that option you will be given the option to choose the partition  you made. Choose "delete partition". You will go to the screen with the partitions again. Choose the now deleted/"unallocated space" partition. Choose the option "automatically partition" available space. The install will partition the drive again into swap and another partition.
The more difficult way is to set up all the mount points yourself. You will have to make the partitions and then choose them with "manually edit " partition table.
When you get to the next screen you will chooose the partition you want. Then you will have options. You must choose the file type i.e. swap, ext3. Then choose what you want it for i.e. home directory, swap, root file system. After you go through all your partitions and set there file type and mount points you write changes to disk. This section of the guide in my link will give you an idea. [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) Good luck.

---

### Post by ComplexNumber on 2006-05-04
>  My question is, how do you specify that you want them on different partitions?
i thought i already answered that :confused:

---

### Post by 3rdalbum on 2006-05-05
Make your swap partition as big as you want, but try not to use more than 1.5* your RAM.

Linux writes swap information to another mounted partition (probably /home) if the swap is too small for the current memory usage, so it's not a *problem* if you make it too small - swapping will just run a little slower.

---

### Post by az on 2006-05-05
[QUOTE=kc0eak]
My question is, how do you specify that you want them on different partitions?

Also, during the installation, do I get to select which partition to put the directories on, or does Ubuntu automatically select which ones to use?

Thanks again![/QUOTE]


I reccommend the default partitioning scheme - all on one paretition plus swap.  You will have a much better time installing and if you ever need to back up your home driver, you still can.  There is no real advantage to putting your home on a different partition.  It is a pain, too, if you run out of space on one of your partition because of that.

The default installation scheme will also work out your swap size for you.  Between 1.25 and two times your ram, depending on how much ram you have versus disk space.   You need at least 1.25 your ram to be able to hibernate.

If you use the live cd for installation (dapper espresso, now know as ubiquity) it can take about twenty minutes (half hour, tops)  to install on a pentium II.

---

### Post by az on 2006-05-05
[QUOTE=3rdalbum]

Linux writes swap information to another mounted partition (probably /home) if the swap is too small for the current memory usage, [/QUOTE]
Huh?

---

