---
title: "Making the switch, need quick partitioning advice"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by astyler on 2008-02-11
So I'm about to switch from Windows to Ubuntu and I had a few questions.

I plan to use it for the following uses:
General desktop -- internet, gmail, etc...
Folding @ Home
TF2 in Wine
Myth master backend

 I have 960GB of drive space, how should I do my partitions?

I understand mounting swap/ for about 2-3GB or so.
Where will wine, TF2 or other windows games go? On / or home/?
How much space should I mount for home/?
Do I need a boot/ mount?
Finally, I want to mount var/lib/ as most of my space for recordings.

swap/ - 3GB
/ - 15GB
home/ - ?
var/lib/ - rest

Thanks for any and all help.  I'm likely going to set up an LVM for var/lib/, but I just wasn't sure on sizes for / and home/, depending on where my apps go (TF2 is probably around 4 GB alone)!
__________________

---

### Post by njparton on 2008-02-11
As a minimum you'll need the following partitions:

/swap
/home
/

If you've got a healthy amount of RAM then 3GB may be a bit OTT.  If you plan to suspend to RAM, just make sure your swap is at least as big as your total RAM. Linux is very good with the swap file and you'll hardly ever notice it being used.

For "/" I'd go for a 10Gb partition and then a larger partition for "/home", say 50-100Gb.

It's up to you though and if you go with the ext3 filesystem then you can resize your partitions later.  Just reduce the size of your NTFS partitions in windows first to free up space to be on the safe side.

---

### Post by hyper_ch on 2008-02-11
> **astyler said:**
> 
swap/ - 3GB
/ - 15GB
home/ - ?
var/lib/ - rest


swap -->1x - 2x your ram.
/ (root) --> 15 GB are fine, maybe make it 20 GB just to be totally fine ^^
/home --> all the rest you want to spare

---

### Post by harold4 on 2008-02-11
Here is my laptop setup.

40gb Windows (NTFS)
10gb / (ext3)
15gb /home (ext3)
2gb (swap)
170gb /media/storage (fat32)

---

### Post by astyler on 2008-02-11
great, thanks for your help.  I guess it indirectly tells me that my apps will be going in /home and not / so I'll partition accordingly.

:)

---

### Post by asmoore82 on 2008-02-11
IMHO, advanced partitioning schemes are only helpful if you have multiple hard drives.

if all of the partitions are to be on one gigantic drive, I would just leave it one partition
(except for Swap, of course) or you will be seeking your heads to death.

/home on a separate partition has its purpose if you are going to be replacing the OS often
and have no other way to back up data, but 500GB external drives are available for ~$100

---

### Post by ferdostar on 2008-02-11
> **astyler said:**
> So I'm about to switch from Windows to Ubuntu and I had a few questions.

I plan to use it for the following uses:
General desktop -- internet, gmail, etc...
Folding @ Home
TF2 in Wine
Myth master backend

 I have 960GB of drive space, how should I do my partitions?

I understand mounting swap/ for about 2-3GB or so.
Where will wine, TF2 or other windows games go? On / or home/?
How much space should I mount for home/?
Do I need a boot/ mount?
Finally, I want to mount var/lib/ as most of my space for recordings.

swap/ - 3GB
/ - 15GB
home/ - ?
var/lib/ - rest

Thanks for any and all help.  I'm likely going to set up an LVM for var/lib/, but I just wasn't sure on sizes for / and home/, depending on where my apps go (TF2 is probably around 4 GB alone)!
__________________

Just one think, before managing your partitions make a backup! Otherwise you can follow the others posts ;)

---

### Post by asmoore82 on 2008-02-11
another concern to consider when deciding what will be on a separate partition is:

What if the unthinkable happens and all partitions become unmountable except the root?
Will the system still be able to fully boot up?

From this angle, /home is extremely safe to be on another partition,
but /var... could go either way, and /etc would be certain death.

remember that if a mountpoint fails, the folder will still exist, but it will be empty.

---

### Post by bigredradio on 2008-02-14
> **asmoore82 said:**
> IMHO, advanced partitioning schemes are only helpful if you have multiple hard drives.

if all of the partitions are to be on one gigantic drive, I would just leave it one partition
(except for Swap, of course) or you will be seeking your heads to death.

/home on a separate partition has its purpose if you are going to be replacing the OS often
and have no other way to back up data, but 500GB external drives are available for ~$100

A more likely point of failure is filesystem corruption than disk failure. Breaking up the system into different filesystems is the safest choice. / /var /usr /home /tmp. If any of the filesystems (other than /) fail, you will still be able to get to a shell and perform some filesystem repair. As far as the seeking issue? I would think that building a filesystem on one large device would be worse. If you utilize the space and keep partitions that do not change often separate (like /usr or / ) then any non-contiguous data is limited to certain sections of the disk. I might be wrong, but in my experience, creating separate filesystems is the way to go. Using LVM is even better so that you can resize the filesystems as needed.

---

