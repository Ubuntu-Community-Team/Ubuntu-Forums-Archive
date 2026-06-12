---
title: "hard drive partitioning"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-02-25
I would like to install ubuntu on my laptop as a dual boot with Windows XP.  Is the creating of the necessary partitions done for me or is that something that I have to do before installing ubuntu?

Also what is the best way of doing this, the classic method ie booting from the ubuntu cd, or using the cd that allows you to install from within windows?

Thanks

---

### Post by tribble222 on 2007-02-25
If you currently have 1 hard drive and only 1 partition, then you will need to create a 2nd partition while you install ubuntu.  I like installing from the livecd best (boot into the cd and click install). During the install process it will ask you how you want to partition your drives and that is where you choose your options.  If you are going to shrink your windows partition to a smaller size to make room for a new ubuntu partition, then make sure you thouroughly defrag your windows partition first.

Also, before you do any kid of patitioning to your drive make sure you have everything fully backed up in case anything goes wrong!

---

### Post by victorbrca on 2007-02-25
I would do it manually.... Gives you more options

Take a look at this site... gives u screenshots and everything...

[Pschocats]("http://www.psychocats.net/ubuntu/installing")

Vic.

---

### Post by chris.olsen on 2007-02-25
I did do a defrag, and after noticed that the files are not "clumped" in one section of the drive.  There is no longer any fragmentation, but isn't any other large chunks of hd space.  Will the partitioner take care of this, or will I be severely limited in the size of the partition that I am able to create?

Thanks for the quick tips.

edit

i see from the screen shots that it can shrink the windows partition.  Thanks for the link.

---

### Post by victorbrca on 2007-02-25
I ran defrag more than 5 times when I first installed a dual boot. Windows defrag sucks... BTW, make sure u run "disk cleanup" first...


Vic.

---

### Post by chris.olsen on 2007-02-25
any estimates on the minimum size of hard drive required to setup windows and ubuntu on the same drive.  I currently have an 80GB.  I am just not sure with all the extras that ubuntu requires ie swap drive

---

### Post by george29 on 2007-02-25
For winXP - depending on what software you want installed, games, office etc, anywhere from   15 - 30Gb should be sufficient (primary partition). For Ubuntu 15Gb for OS, use 512MB as swap - if you have more RAM than 512MB you will probably hardly use the swap space (in an extended partition). then use the rest of the drive in a primary partition as storage for data to share between XP and ubuntu.

---

### Post by victorbrca on 2007-02-25
An 80G is more tan enough. Now it just depends on how much u wanna use for Ubuntu. You will need a min. of 2 partitions for Linux, 1 for the system which / (same as C: ) and another for ur swap (which should be twice the size of ur RAM). You can also use a 3rd partition for your home folder (same as my documents).

My laptop has 60GB, and I had it like this (no separate home partition):

Primary - 45GB - Windows
Primary - 10GB - Linux - /
Secondary
                  - Logical - 2GB - Swap
                  - Logical - 3GB - FAT32 for swap between 2 OS



Vic.

---

### Post by chris.olsen on 2007-02-25
To create the FAT32 to allow for file sharing between the OS's I take it you had to manually configure the partitions to do that.  Having that ability would be nice.

---

