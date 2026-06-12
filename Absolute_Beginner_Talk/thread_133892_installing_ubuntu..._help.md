---
title: "installing ubuntu... help"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by maka on 2006-02-20
Hi, 

im new to this linux thing so please help me out.

i was introduced to this ubunto from my cousin.  i tried to live cd and i liked hjow it looked.  i was wondering how i can install ubunto as a separate os on my computer so that when i boot it up, i can run either windows or ubunto.

my computer is currently running windows xp home.

i would appreciate any kind of help or explaination in how it will work. :p 

thanks,
maka

---

### Post by amoser on 2006-02-20
Well, you need to make room on your hard drive, which if you have Partation Magic, it shouldn't be a problem.  Then install Ubuntu into the free space, and let the installer do the rest.  The only thing that you woud have to worry about, is when it asks you where to install GRUB (at the end of the install process) make sure you install it to your MBR

---

### Post by aysiu on 2006-02-20
See the fifth link of my signature. You won't regret it.

---

### Post by maka on 2006-02-21
wow thanks for the link, it was really helpful.

now, I was just wondering how things exactly worked.  for example, i have programs already installed on my windows, say a game.

so after i partition my computer where both os's can read and write to each another...can i run the program which was initially installed on windows when im running Ubuntu?

also, i was wondering i have about 70 gigs free on my hd and my file system is currently NTFS.  So im doing the Ubuntu + NTFS option.  in one of the steps, the windows partition was made 20 gigs smaller.  So there was 20 gigs free for a partition, but only made a 10 gig partition fat32 for ubuntu.  So there was still 10 gig free where in **STEP 22.4** they clicked the option "Automatically partition the free space".  I'm not too sure what that was about.. If i reduced my windows partition by 20gigs, can i just create the fat32 partition for ubuntu to be 20gigs?

sorry for the noob questions.. i just really want to install it and use it after seeing it from the live cd :-D 

oh forgot one more thing... my computer's processor is amd athlon 64, 3200+.  does that change anything? just in case.

thanks in advance,
maka

---

### Post by metavo on 2006-02-21
My computer gets stucked during the installation while configuring powernowd. 
Version of Ubuntu is 5.10
I'm trying to run it with
AMD Athlon 3000+
GeForce 6600GT
ECS nForce4-s939 
Any help?

---

### Post by Coelocanth on 2006-02-21
[QUOTE=maka]wow thanks for the link, it was really helpful.

now, I was just wondering how things exactly worked.  for example, i have programs already installed on my windows, say a game.

so after i partition my computer where both os's can read and write to each another...can i run the program which was initially installed on windows when im running Ubuntu?[/quote]

No, I don't believe that will work, as I believe you need WINE installed and have to load the program into Ubuntu. I could be wrong there though. I haven't tried it.

> also, i was wondering i have about 70 gigs free on my hd and my file system is currently NTFS.  So im doing the Ubuntu + NTFS option.  in one of the steps, the windows partition was made 20 gigs smaller.  So there was 20 gigs free for a partition, but only made a 10 gig partition fat32 for ubuntu.  So there was still 10 gig free where in **STEP 22.4** they clicked the option "Automatically partition the free space".  I'm not too sure what that was about.. If i reduced my windows partition by 20gigs, can i just create the fat32 partition for ubuntu to be 20gigs?

No. What happened there is you created a FAT32 partition to which both Windows and Ubuntu can read and write files. The option to automatically partition the free space is going to take the other 10 GB and install your Ubuntu root partition, your swap file, and your Ubuntu main partition. Ubuntu won't install onto a FAT32 partition, from what I've read. You'll need to choose between ReiserFS, ext2, or ext3 formats (IIRC) for your Ubuntu installation (I chose ext3).

> sorry for the noob questions.. i just really want to install it and use it after seeing it from the live cd :-D 

Don't be sorry. Everyone was a noob once (I still am, having installed Ubuntu only about 2 weeks ago).

> oh forgot one more thing... my computer's processor is amd athlon 64, 3200+.  does that change anything? just in case.

thanks in advance,
maka

No. My system's an AMD Athlon 64 3200+ as well. I've encountered no processor related problems.

---

### Post by maka on 2006-02-21
[QUOTE=Coelocanth]
No. What happened there is you created a FAT32 partition to which both Windows and Ubuntu can read and write files. The option to automatically partition the free space is going to take the other 10 GB and install your Ubuntu root partition, your swap file, and your Ubuntu main partition. Ubuntu won't install onto a FAT32 partition, from what I've read. You'll need to choose between ReiserFS, ext2, or ext3 formats (IIRC) for your Ubuntu installation (I chose ext3).[/QUOTE]

thanks for the response.  so say instead of creating the fat32 partition to be 10gb like the guide did, if i chose 30gb for the partition, is 10gb enough for the swap file, so totalling 40gb freed from the windows partition

or would i have to match the size of the partition for ubuntu, 30gb for partition, 30gb for swap file (total 60gb freed from windows partition).

thanks,
maka

---

### Post by Herman on 2006-02-21
maka, the example install begins with a 30.0 GB hard disk which is all one big Windows partition.
Then it shows how to tell the computer Windows can only have 10.0 GB.
This gives us 20.0 GB of free space to divy up. 

Then 10.0 is taken and made into a FAT32 partition for sharing files between Windows and Ubuntu. Another name for a partition when it will be used in this way is a 'data' partition. You may make your data partition any size, some like them big, for example you may want to make it as large as possible and just leave the last 4 or 5 GB for the main Ubuntu partition. Others like them small, maybe 1.0 GB for their data partition, if they only want to use it for a sort ot a 'depot' or transit point for a few small files being passed from one system to the other.

Then whatever space is left over, is automatically partitioned by the Ubuntu installer. The Ubuntu installer will make a ext3 main (operating system) partition, plus a small 'swap' area automatically for you.

In Linux, a 'swap area' is another small partition, usually two or three times the size of your computer's RAM, for the operating system to shunt slow moving stuff that's in the road out of the RAM for a while to leave room for the hi-speed stuff to zoom in and out of the memory very fast. Mosty they don't seem to actually use much of the memory swap area under normal use, but it still seems to make a big difference to have at least a small swap area.
You won't need to worry, the installer will do that automatically if you choose that option. If you want to do it manually, you can, it's okay, but you'll only need maybe 1.0 GB of swap probably, not 30.0

er...I have to leave right now in rather a hurry , will be back later, I hope that will be enough to help you along a bit....

---

### Post by Herman on 2006-02-21
...continued
 > so say instead of creating the fat32 partition to be 10gb like the guide did, if i chose 30gb for the partition, is 10gb enough for the swap file, so totalling 40gb freed from the windows partitionYes, you could make 40.0 GB free space from Windows if you want, and then make 30.0 GB of that for your fat32 data partition, leaving the last 10.0 GB to be automatically partitioned into say 9.5 ext3 (your Ubuntu system), plus .5 GB (memory) swap area for example.

Or if you want you could do it the other way around and make your 40.0 GB divided up as 10.0 GB fat32 data partition for file sharing plus 30.0 GB automatically partitioned as ext3 and a small swap area. (for the memory).
It's up to you it depends on how you want to use your computer, maybe it won't matter much until you try it out just any old way, and after you get a little experience you can use GParted to resize your partitions later on if you want. :-D  (Herman)

---

### Post by dvarsam on 2006-02-21
... and by the way:

To be able to view & work on Open Office Org's "Writer" files in the Windows Microsoft's "Word" world, ALL files MUST be saved in the ".doc" format instead of the DEFAULT "odt" format (in the Ubuntu side).

When I realized that, I had to RE-save EACH & EVERY file I created in "Writer" in the ".doc" format to make it work in Windows MS "Word"...
That was a pretty "time-consuming" procedure for me - because my files were many...

---

### Post by Coelocanth on 2006-02-21
Maka, it looks like Herman pretty much covered it, but I'll show you what I did with my system when I installed Ubuntu about two weeks ago:

I have a 250 GB SATA drive, which had Win XP installed on one big partition (the whole 250 gigs). I resized it using the Ubuntu install disk so that WinXP now owns 200 GB of the hard drive. Of the 50 GB I freed up, I made a 15 GB FAT32 partition so I could share files between Ubuntu and XP. The remaining 35 GBs, I let the install decide for me. It ended up with the root partition, about 1.5 GBs of swap (I have 1 GB of RAM in the box), and the rest for the main Ubuntu install.

I plan on grabbing a second hard drive in the next couple weeks or so and I'll install Dapper on that when it's released, as I've decided to make the switch from Windows completely (I still have to keep the XP install, as my wife doesn't want to learn a new OS and she needs XP for some work-related stuff). I'm basically using Breezy as a test drive and I'm trying all kinds of different things with it to learn how to use Linux. If I 'break' it or fubar it, I don't mind since I'm trying to learn from it. (In light of that, I probably didn't need to partition the way I did, but I now have a better idea what I'll do with Dapper.) Hopefully, I'll know enough about Linux to be able to install Dapper the way I want it and be able to set it up with little problem when it's released in April.

---

### Post by sohailubuntu on 2006-02-23
[QUOTE=aysiu]See the fifth link of my signature. You won't regret it.[/QUOTE]


Great link, I just installed ubuntu on my pc and used the instructions from the link. However the ubuntu boot cd wasn't partitioning my drive properly. It wasn't resizing my existing partition, so I used partition magic to create partitions then I used the CD to install ubuntu.

---

