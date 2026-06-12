---
title: "A couple of instalation questions."
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mattyatty on 2007-06-13
I'm planning on installing ubuntu for the first time tomorow (its my first time installing any OS) , and I'm about to burn the disk, and I just want to check a couple of things:

What is the best speed to burn the disk at (I don't want it to take hours, but at the same time I don't want errors)

When I burn the disk, in the settings, I need to make the disk "Bootable" don't I?

I'm doing dual boot with windows, and I don't know how much space to alocate to each. I'm intending on using ubuntu as my main OS for general day to day stuf, but I need windows for gaming. any suggestions (i have a 120GB HDD)?

---

### Post by Anonii on 2007-06-13
Greetings, sir

I'd suggest the usual ISO burning speed, which is 4x (quite slow, yes. But error-proof.)

I know what you mean. But I never toggled by disk as Bootable when I burned ISOs. I think that your best bet, would be to follow this guide: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and you will have no problems.

I'm doing the same thing (but well, I'm quite the hardcore gamer so I don't touch Linux that much anymore (things will change tho >:) ), and my disk is formatted like this:
20GB Windows Partition
40GB Linux partitions
20GB Shared Partition (where I store my Music and stuff, to be accessible from both OSes)

Good luck, and post back any questions.

---

### Post by ts51 on 2007-06-13
[http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO](http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO) 

These screencasts should help. I have installed Ubuntu yet, by I've gotten that far. :)

---

### Post by gauravp55 on 2007-06-13
Burn Speed: 4x is just fine.(It is slow but it won't give u errors)
U can burn the ISO image using a utility such as ISO Burner and your disk would be a bootable one. Don't worry about that.

Ok as far as the allocation is concerned, I reckon abt 10-15 GB (MAX 20 GB) should be sufficient for Linux (7 OR 10 GB Root+ 1 GB SWAP+ 2 OR 4 GB FAT32 SHARED) . Of course if ur gonna be installing a lot of apps on Linux u could always throw in more allocation space for linux.. 

I have a 40 GB HD and I use XP with Ubuntu. I've kept 25 GB for Windows and 10 GB for Ubuntu(7 GB Root , 1 GB SWAP, 2 GB SHARED).

Dual booting shouldn't be a problem at all.. Since  u have a 120 gig HD u could keep a 100 gigs for Windows and 20 gigs for Linux which would be more than sufficient. remember however not to allocate more than a gig for SWAP. That's very sufficient.

Cheers..

---

### Post by az on 2007-06-13
If Ubuntu is going to be your main OS, give ti a lot of hard disk space.

Use the Windows ext2 driver so that you can access your linux partition from windows without having to make a seperate storage partition.  It makes ext2-ext3 filesystems appear as any other windows filesystem in windows.  You get stable read-write functinoality.  It's found at fs-driver.org

---

### Post by mattyatty on 2007-06-13
OK, thanks guys. one more quick question, If I'm installing ubuntu on a brand new computer, is there realy any need to disk defrag before partitioning??

---

### Post by annda on 2007-06-13
it won't hurt. if the windows installation is 'clean', defragmenting will take very little or no time.

---

### Post by Anonii on 2007-06-13
> **mattyatty said:**
> OK, thanks guys. one more quick question, If I'm installing ubuntu on a brand new computer, is there realy any need to disk defrag before partitioning??
No. Your disk is empty, there are no fragmented files.

---

### Post by Inxsible on 2007-06-13
> **mattyatty said:**
> OK, thanks guys. one more quick question, If I'm installing ubuntu on a brand new computer, is there realy any need to disk defrag before partitioning??
 
Defragging Windows partitions is always a good idea, since the native windows file systems are prone to fragmentation. Of course since its a new install, it wont be that much of a problem

---

### Post by Inxsible on 2007-06-13
Wow..2 replies before I could finish :rolleyes:

---

### Post by mattyatty on 2007-06-13
Thanks again, I have one last question. I have just burned the CD, and despite telling it to burn at 4x, it decided to take a mind of its own and burn at 16.1x. Is there any way to scan it to see if there is any problems, or should I just burn a new copy?

---

### Post by Inxsible on 2007-06-13
> **mattyatty said:**
> Thanks again, I have one last question. I have just burned the CD, and despite telling it to burn at 4x, it decided to take a mind of its own and burn at 16.1x. Is there any way to scan it to see if there is any problems, or should I just burn a new copy?
Boot up with the Cd and it will give you a menu. One of them is Check CD for errors , or something to that effect. Use that option and it will tell you if the CD is ok or not

---

### Post by mattyatty on 2007-06-13
Thanks, you've all been a great help!!!!!

---

