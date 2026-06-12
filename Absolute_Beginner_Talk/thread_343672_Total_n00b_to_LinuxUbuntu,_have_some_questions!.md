---
title: "Total n00b to Linux/Ubuntu, have some questions!"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by stephentyler20 on 2007-01-21
I'm sorry if this posts twice, I can't find the original post!

Basically I've used Windows XP Sp2 on my relatively new laptop successfully with no problems. I'm about to attempt Ubuntu, as my first experience with ANY linux. I have a 60 GB harddrive, not partitioned, with 15.5 gb free space. Is this enough? I also have no idea about partitioning hard drives or anything, and it's my understanding that this is necessary. Does the Ubuntu installer make this obvious? If I need to free up harddrive space I can do that, or if it's extremely wise to clear the slate and do it from scratch, that's an option too, but I'd prefer not to. Any other advice? Thanks!

---

### Post by ComplexNumber on 2007-01-21
i would slect custom partitioning and partition 15.5gb as follows:
-assign about 8gb to "/"(root) partition
-assign about 7gb to your /home partion. its useful to have a seperate partition for yu home directory because it can be used as a permanant storage area for documents and mp3's etc. if you ever need to do a fresh install and use another distro,  it means that all your documents and settings stay the same between installs.
-for swap space(ie its called virtual memory in windows), the general rule is to have a swap partition to be twice the size of the amount of RAM on your system. however, if you have lots of RAM, its not necessary to double it. i have 384MB of RAM with a swap of about 700MB, and i've never even used a fraction of that. therefore, i would suggest that you assign about 500MB to you swap partition.

don't bother with having a separate partition for /boot or anything else. store the boot on the MBR.

---

### Post by 56phil on 2007-01-21
Hi, welcome to Ubuntu.

The install process will handle all that hdd stuff for you. 15 Gig is a little tight yet sufficient. 

You may try to do a defrag before you install Ubuntu.

My first install was with XP and it was OK. However, I was so pleased with Ubuntu that I went back and did a clean install, never looked back.

Good luck.

---

### Post by redDEADresolve on 2007-01-21
Yes DEFRAG it's extremely important.

---

### Post by Bachstelze on 2007-01-21
Yep, definitely do a defrag, it could save you trouble but that doesn't mean you can do without proper backups, so do backup any valuable data, too !

Also, don't rsize your Windows partition to the minimum possible, leave a couple of gigs on it (10 GiB is far more than enough for Ubuntu anyway).

---

### Post by stephentyler20 on 2007-01-21
> **ComplexNumber said:**
> don't bother with having a separate partition for /boot or anything else. store the boot on the MBR.

What's the "MBR"? Also, with this manner, I won't have even a drop of free space left for Windows, right? Isn't that kind of problematic?

---

### Post by Bachstelze on 2007-01-21
The installer lets you choose the size you want to shrink your Windows parititon to, just leave it a couple of gigs and you should be fine.

---

### Post by old_geekster on 2007-01-21
> **stephentyler20 said:**
> What's the "MBR"? Also, with this manner, I won't have even a drop of free space left for Windows, right? Isn't that kind of problematic?
"Master Boot Record".  This is a file in the first sector of your drive.  It holds all of the boot information for the system.  Ubuntu uses this space to setup the GRUB (GRand Unified Bootloader), which allows you to chose which OS you want to run.

Yes, you are correct.  Windows requires at least 15GB of free space for most of its tasks, such as, defragging your HDD.  Therefore, you may run into some problems.

You can run Ubuntu from the installation disk.  This will allow you to get your feet wet.

---

### Post by rccharles on 2007-01-22
> **stephentyler20 said:**
> I'm sorry if this posts twice, I can't find the original post!

Basically I've used Windows XP Sp2 on my relatively new laptop successfully with no problems. I'm about to attempt Ubuntu, as my first experience with ANY linux. I have a 60 GB harddrive, not partitioned, with 15.5 gb free space. Is this enough? I also have no idea about partitioning hard drives or anything, and it's my understanding that this is necessary. Does the Ubuntu installer make this obvious? If I need to free up harddrive space I can do that, or if it's extremely wise to clear the slate and do it from scratch, that's an option too, but I'd prefer not to. Any other advice? Thanks!

The install takes around 2.2 gig.  

I'd reserve 6gig for Ubuntu. There are two meanings for free space.

1) Space within a partition 
2) Space on a harddrive without a partition.

If you create space on a harddrive without a partition, you can have Ubuntu allocate the unpartitioned space.

Robert

---

