---
title: "First Ever Linux Install"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by devil_dobie on 2005-11-05
Being as this is my first post, I would like to say that the site is full of great information and people.  I look forward to learning a lot from all of you.

I did a serch, but found a lot of the results somewhat confusing.  I am about to undergo my first ever Linux install (Ubuntu).  I have XP/SP2 now and would like to keep it.  I am very unclear about the necessary partitions.  I would like to dual boot it; with XP on 1 partition, Ubuntu on another, and all of my files on yet another.  I understand that I'll need a swap partition; I don't fully grasp why.  I have 1G RAM, and I think that translates into 1.5 - 2 gig swap.

The HD is 80G and I would like only Windows files on the XP partition, only Ubuntu files on the Ubuntu partition, and all other files on the "file" partition so that they can be accessed from both OSs.

I appreciate any and all advice that you all may provide.  Thank you in advance.

---

### Post by blackant on 2005-11-05
I am like you, switch from Windows to Ubuntu this year.. :P
But I clear off windows once and for all. Never look back now.

Give up all the games too.. hehehe

---

### Post by Kyral on 2005-11-05
Hmm, first I'll tackle the Swap issue, and quick explination where Swap came from

*clears his throat*

Okay, back in the day (We are talking mid 80s - early 90s.....crap that makes me feel old) computers didn't have the massive amounts of RAM that they have now, and sometimes they would run out. Now this is obviously very bad. So the Unix folks (and recall that Linux is decended from Unix) had a really cool idea for the time. Lets use a part of the hard drive as RAM just in case. This was the birth of the Swap partition. Now, obviously, swap is much slower than RAM, and was only intended as an emergency measure. Now fast forward to the present time. Linux is around, and we have desktops with RAM going out around 2 GB in some cases. Yet the Swap is still around. Well, in those cases swap isn't really needed. So there is a general formula for Swap.

if you have less than 512 MB RAM, then you should make your swap about twice the size of it.

If you have between 512 MB and 1 GB, then you should make the swap 1.5 times the size of it.

If you have more than a GB, then you can either forget swap, or make it 512 MB.

As for partitioning....here is something I can see

20 GB NTFS (Windows)
10 GB Linux (ext3)
512 MB SWAP
rest (FAT32) Shared

---

### Post by Cufishing on 2005-11-05
I don't want to hijack this thread, but I have a question that I believe that does not require a new thread.
Kyral, may I ask, what is the difference between a (FAT 32) Shared. And a Windows Virtual Fat (vfat)?

---

### Post by Kyral on 2005-11-05
There is a difference? I always used them interchangably. Heck when I write an fstab I use vfat to refer to FAT32

---

### Post by gord on 2005-11-05
FAT 32 was introduced in windows95 osr2, vfat was used in windows 3.11 and windowsNT 3.1 (allthough slightly diffirent and under a diffirent name). i have a niggling feeling i might be wrong with this. but i think vfat is essentially FAT 16 with long filename support.

---

### Post by majikstreet on 2005-11-05
[QUOTE=Kyral]There is a difference? I always used them interchangably. Heck when I write an fstab I use vfat to refer to FAT32[/QUOTE]
they seem the same. vfat may be the way linux refers to them, while MS may call them FAT 32.

---

### Post by PatrickMay16 on 2005-11-05
[QUOTE=devil_dobie]Being as this is my first post, I would like to say that the site is full of great information and people.  I look forward to learning a lot from all of you.

I did a serch, but found a lot of the results somewhat confusing.  I am about to undergo my first ever Linux install (Ubuntu).  I have XP/SP2 now and would like to keep it.  I am very unclear about the necessary partitions.  I would like to dual boot it; with XP on 1 partition, Ubuntu on another, and all of my files on yet another.  I understand that I'll need a swap partition; I don't fully grasp why.  I have 1G RAM, and I think that translates into 1.5 - 2 gig swap.

The HD is 80G and I would like only Windows files on the XP partition, only Ubuntu files on the Ubuntu partition, and all other files on the "file" partition so that they can be accessed from both OSs.

I appreciate any and all advice that you all may provide.  Thank you in advance.[/QUOTE]
Ah, my friend... This may help you.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

As for the "file partition" that both OSes can access, you should FAT32 for that partition.

By the way, just as a safety precaution: Make sure you have the Windows CD and other things you'll need to install Windows in case something goes wrong and your current installation of Windows breaks. It may not be likely to happen, but it's good to be on the safe side.

I hope you have a great experience with Ubuntu.

---

### Post by tageiru on 2005-11-05
[QUOTE=Kyral]Now fast forward to the present time. Linux is around, and we have desktops with RAM going out around 2 GB in some cases. Yet the Swap is still around. Well, in those cases swap isn't really needed.[/QUOTE]
This is not entirely accurate. With the current implementation of the VM-system in the kernel swap may in fact increase the computers performance even if you never run out of ram.
[QUOTE=KernelTrap]Nick Piggin explained that swap can improve performance no matter how much RAM you have, "well it is a magical property of swap space, because extra RAM doesn't allow you to replace unused memory with often used memory. The theory holds true no matter how much RAM you have. Swap can improve performance. It can be trivially demonstrated." This said, numerous Linux users do report success running a swapless system.[/QUOTE]

[http://kerneltrap.org/node/3202](http://kerneltrap.org/node/3202)

---

### Post by patrick295767 on 2005-11-05
[QUOTE=blackant]I am like you, switch from Windows to Ubuntu this year.. :P
But I clear off windows once and for all. Never look back now.
   
Give up all the games too.. hehehe[/QUOTE]
   
Games games ...
did you try winehg /crossover :
   
I saw that halflife is EVEN working:
did you try if it's playable (not laggy) ?
[http://appdb.winehq.org/appview.php?versionId=2049](http://appdb.winehq.org/appview.php?versionId=2049)
    
Greetings !!
    
   
_______________
Linux is soo stable, I love burning DVD via nfs server_pc without ANY burning failure !!

---

### Post by Plank117 on 2005-11-05
It's generally good practice to defrag your winows partition and then use something like PartitionMagic to allocate a new partition. The Ubuntu installer will walk you through the process of installing it on that partition and setting up a dual boot. By the way: One of us! One of us! One of us!

---

