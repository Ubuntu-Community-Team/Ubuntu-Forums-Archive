---
title: "Partition/dual boot questions"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2006-10-30
Ok, I want to install Ubuntu on my computer, which has Windows XP already installed.

I was told by a Linux user that the best way to do it is to set up your partitions manually with the installer on the LiveCD.

So my question is: How many partitions do I need, and what size should they be? I want simple step by step instructions on how to do this, just to make sure that I don't mess it up.
(Getting a 'clean start' is out of the question, because this is a shared computer with other peoples files on it.)

---

### Post by Coelocanth on 2006-10-30
You only need 2 partitions: / (root) and swap. However, many people like to have /home on a separate partition as well. So, you could go with /, /home, and swap.

For your swap partition, a general rule of thumb is the same amount as your RAM, if you have a decent amount of RAM. 1.5x or 2x your RAM if you have only a moderate amount.

As for the other partitions: it's completely up to you, but you've given no information on how much space you have available, so suggestions are rather difficult.

---

### Post by ahaslam on 2006-10-30
I'd recommend a minimum 5G root (/) partition, a swap partition at 2xRAM (max of 1G) & a home partition large enough to store all of your personal files. 

Of course it's totally down to you, you could just use one 5G partition & be done with it (you don't *need* swap on a desktop).

I hope that helps.

Tony.

PS. I'd recommend the ext3 filesystem.

---

### Post by Hobo Joe on 2006-10-30
Ok, so the root partition would be the one that has Windows on it?
And what is the swap partition? I have 1.5 GB or RAM, would that be  enough?

The basic structure that I would like to have is Windows on one half, and Linux on the other.(I have a 200GB HDD) And then if there are any other small ones I need I could add those to.

---

### Post by ahaslam on 2006-10-30
Your root (/) partition is where Ubuntu itself resides, along with installed applications.

If you wanted it to function in a similar way to Windows, you can do without the separate /home partition & have your personal stuff on the same partition as the system stuff.

You have a good amount of RAM, so I'd limit swap to 1G max.

So for you, I recommend a 100G root (/) partition and a 1G swap partition.


Tony.

PS. Just to complicate things (sorry) you may wish to add a FAT32 partition. This would be a place where you could store files that you require full read/write access in both Windows & Linux.

---

### Post by bulldog on 2006-10-30
Make a / (root) partition of about 10-12GB so you can install programs without having not enough space.

Make a swap 1GB

Make a /home from the rest of your space.

When you have to do a reinstall you won't lose your personal data which is on your /home partition.

Start with defragmenting windows several times so the files are nice on a row.
Then boot the live cd and push the install button on your desktop.

The rest is shown on screen,till the partitioner,then create your partitions as shown above. 

Succes.

---

### Post by Hobo Joe on 2006-10-30
Wait, so your saying that Windows and Linux should both be on the same partition?
Or would it be good to do the 'automatic' one that's in the installer?

I would like to be able to acess music/pictures in both Windows and Linux.

---

### Post by Hobo Joe on 2006-10-30
> **bulldog said:**
> Make a / (root) partition of about 10-12GB so you can install programs without having not enough space.

Make a swap 1GB

Make a /home from the rest of your space.

When you have to do a reinstall you won't lose your personal data which is on your /home partition.

Start with defragmenting windows several times so the files are nice on a row.
Then boot the live cd and push the install button on your desktop.

The rest is shown on screen,till the partitioner,then create your partitions as shown above. 

Succes.

Thanks for the nice simple response. But I still need to know which one that Windows would be on.

Would it be Windows on the /home?

It would be really nice if someone could give me like...a graph or something.

---

### Post by bulldog on 2006-10-30
Nope they go on separate partitions.

The partitioner will ask you what to do,just make your windows partition smaller so you get space for Ubuntu.

This space you gonna use for your '/' , 'swap' and /home partitions.

Edit:
Do you have one large partition for your windows?
Or do you have more partitions like d:\ e:\ and so on.
It's important you make this right.

If you want a graphical interface just download the gparted ISO and burn it on a cd.

Boot this cd and you have a perfect interface to partition the drive as shown above

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Hobo Joe on 2006-10-30
> **bulldog said:**
> Nope they go on separate partitions.

The partitioner will ask you what to do,just make your windows partition smaller so you get space for Ubuntu.

This space you gonna use for your '/' , 'swap' and /home partitions.

Edit:
Do you have one large partition for your windows?
Or do you have more partitions like d:\ e:\ and so on.
It's important you make this right.

If you want a graphical interface just download the gparted ISO and burn it on a cd.

Boot this cd and you have a perfect interface to partition the drive as shown above

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I just have 1. (as far as I know at least, I know I haven't edited it before.)

Since I have a 200GB HDD, could I do something like 100 GB for Windows, and 100GB for Linux, and then 1 GB for the 'swap'?(roughly)

---

### Post by bulldog on 2006-10-30
If you have the space available,yes you could.

But defragment windows several times in a row **before** you begin!!

Then bootup the live cd and give it a go.

When you going to make space for ubuntu by making your windows partition smaller,look carefull you **won't** format your windows.

In the space you create you can make your ubuntu partitions.

You can let ubuntu take care of everything though,but most of the times you gonna change it later.

If you let ubuntu take care of things,choose the option for that,not the option to use the whole harddisk though,then it will wipe your windows :D

---

### Post by 29er on 2006-10-30
Hi Hobo,
I'm a newbie like you esp at dual boot. But found a really easy way to set it up initially, you can always reset it later if you want. I have a 60 G hd and was rebuilding my XP (again) so gave it half (30G) and left the rest as unallocated. tip: use my "computer>manage>disk manager" for this, it's a lot easier than the "partition prepare" on the Kubuntu live CD. Then when Kububtu loads use the auto setup option for sizing partitions (the middle option) I'll go back next week and reset some of those fields like /, /swap, and /home, but at least I'm up and running. My setup as
c: winxp - primary drive
d: windata - extended partition with logical drives
e: fat32 transfer partition
hda2 /root - primary
hda7 /swap - primary
hda8 /home - extended partition c/w logical

linux uses hda1,2,3,4 for primary drives
hda 5 etc for logical drives so in linux
c: is hda1
d: is hda5
e: is hda6

Linux can see extended partitions but not multiple drives in those partitions, maybe someone out there can correct me if I'm wrong. Hope this helps.

---

### Post by Coelocanth on 2006-10-30
I have a 250 GB SATA drive, and when I installed Ubuntu, I did the following (I'd do it a bit differently now that I know more, but it serves me well for the nonce):

Originally, Windows was on 1 partition, taking up the whole drive. I resized the partition, shrinking Windows to 200 GB. That left me with 50 GB of unallocated space. I made a 15 GB FAT32 partition that would allow me to share files between Windows and Linux (since they can both read that file format).

Then, I installed Ubuntu on the final 35 GB of space, using 1 GB for my swap (swap is the same idea as the Windows page file). The rest, I used for /. (Now, I'd use a separate /home partition as well, but I'm going to repartition my disc soon anyway). So, the final result is:

first 200GB = Windows XP
next 15 GB = FAT32 partition.
next 34 GB = Ubuntu / partition
next 1 GB  = swap partition

I plan on shrinking my Windows partition even further, as I rarely use it now, so I can free up another 100+ GB of space. This will give me room to try out some new distros. In this space, I'll definitely set up a separate /home partition.

Hope that makes things a bit clearer.

---

### Post by Hobo Joe on 2006-10-30
Thanks for all the help guys, I think I'm ready now!

---

### Post by Nut on 2006-10-30
Make sure Windows isn't taking up your whole hard drive. Make a swap partition twice the size of your computer's ram, and a ext3 partition with the remaining part of your hard drive.

Easy stuff.

Basically, here are your partitions, with 500 MB ram and a 100 GB hard drive.

**Partition 1 (Windows)**
Size: 50 GB
Type: NTFS (automatically formatted to this type. you don't need to mess with it.)

**Partition 2 (linux file sys)**
Size: 49 GB
Type: ext3
whatchamacallit: / (root)
Primary

**Partition 3 (linux swap)**
size: 1 gb
type: swap (linux-swap)
whatchamacallit: /swap or whatever.
***_[I]when you make the partition it will AUTOMATICALLY make the swap /swap and the ext3 / (ROOT).*_[/I]**
primary

yeah, that's it.

it's actually easier than you think. you really don't need to mess with anything after making the partitions manually on the livecd. it may have more than one partition for windows though. mine doesn't as i installed it myself and i made one partition of  half my hard drive and during the installation it formats it to NTFS itself.

but, that's all you need. as soon as my server gets running i'll let you know of a tutorial i'm going to write of it.

---

### Post by Hobo Joe on 2006-10-30
Ok, I'm running off the LiveCD right now, but I'm having trouble with editing the partitions.  When I click on my HDD, there is no option for a 'new' partition. How am I supposed to do this if I can't make new ones?!

---

### Post by orsula on 2006-10-30
> **Hobo Joe said:**
> Ok, I'm running off the LiveCD right now, but I'm having trouble with editing the partitions.  When I click on my HDD, there is no option for a 'new' partition. How am I supposed to do this if I can't make new ones?!

I just installed Edgy today on a dual boot. I had Dapper before. I simply right clicked and erased the partitions I had before and then added new ones on the gray unallocated space that was created when I erased the old ones. I used to have:
/hda1 - ntfs
/hda2 - swap
/hda3 - ext3

I wanted to installed transfer partition so I erased the older partitions..(don't touch the ntfs though..) and created new ones.

---

### Post by Hobo Joe on 2006-10-30
The 'unallocated space' is only a few MB. And when I click on the drive(it's currently one partition) it won't let me click 'new.'

So I can't proceed at all.....

---

### Post by orsula on 2006-10-30
Assuming you chose during installation to manually alter the partition table, you should be able to see a table with the current partitions. When I said I erased my partitions I didn't choose my HDD, I chose each partition I wanted to alter independently. The LiveCD is using QTparted which allows to resize a current partition as well (right click..). For a dual boot, you must first make room for the new file system. So if you didn't do so, you first need to resize your only partition to allow room. Before you do that, I would defrag a few times the windows partition as was suggested above. QTparted should handle resizing the windows partition without problem. Once that is done, you should have more than a few MB of unallocated space to play with.

---

