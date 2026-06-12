---
title: "Switching to single-boot"
date: 2008-11-12
forum: Apple Hardware Users
---

### Post by sunbird on 2008-11-12
Hi all,

After 13 months on Ubuntu, I think I'm ready to give up my OS X crutch (which I rarely use anyway). I made a bad decision when I installed I did one large partition for / and then a separate swap partition (i.e. no separate /home). I'm thinking about fixing this, getting rid of OS X, and installing a 8.10 install all at the same time. My current partition table looks like this:

```

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   12.0GB  11.8GB  hfs+         Apple_HFS_Untitled_1       
 3      12.0GB  12.2GB  200MB   ext3         boot                  boot 
 4      12.2GB  116GB   104GB                         
 5      116GB   120GB   3813MB               swap       

```

My end goal is to look like this:

```

Letter  Size    
 A      210MB   Boot 
 B      12.0GB  Root FS for Ibex
 C      12.0GB  Root FS for Heron
 D      92GB    /home
 E      4GB     swap

```

(using letters to avoid confusion with partition numbers in old table)

Why do this? My thought is that it'll make it easier to transition from one distro to the next to have separate installs on different partitions.

I wanted to run my plan by folks here to see what I'm forgetting:
[INDENT]
1. (Goes without saying) Backup everything before I start

2. After backing up /home (twice!), delete /home data to free space on the partition.

3. Boot into Ibex Live CD and use gparted to:
[INDENT]
A. Reformat partition 1 as ext3 and copy data from old partition 3 to new partition A.

B. Delete partition 3.

C. Resize Partition B to include old partition 3.

D. Shrink Partition 4 to new partition C (12GB).

E. Create new partition D in free space.
[/INDENT]

4. Install Ibex in Partition B.

5. Modify Grub menu so that 1st bootable is partition B and second is Heron in Partition C.

6. Copy backup of /home to partition D.

7. Modify fstab and other /etc files in Heron install on Partition C.
[/INDENT]

I'll also be following [these instructions]("http://ubuntuforums.org/showthread.php?p=5524612&highlight=single+boot#post5524612") to bless the device and get rid of the mac startup sound.

I guess my specific questions are:
[INDENT]
1. How reliable is partition shrinking? Obviously, everything will be backed up, but the whole point of having two partitions with ubuntu is that I can fall back on Hardy Heron if I have trouble with Ibex following the install. I'd be bummed to end up having to start over.

2. I think that 12GB is probably a bit excessive for a FS partition. How much would you use for a / partition (exclusive of /home)? I guess a related question is whether my swap size of 4GB is excessive (I have 2GB of ram).

3. Wondering if I should maybe do the backup using dd from a live cd to an external drive so I can restore everything exactly as it was before if something goes screwy (rather than my standard rsync).

4. What am I forgetting here?
[/INDENT]

Thanks and sorry for the rambling post...

---

### Post by stir-crazy on 2008-11-12
Don't have extensive experience with partition editing, but from the half dozen or so attempts I've made, I've had good luck in resizing.  Had backed data up, but didn't really need to judging from my end results. :guitar: However, I'm pretty sure all of my resizing attempts were on fresh to semi-fresh installs, so presumably my data was contained in those early clusters.

I'd think 12GB is too big too.  Probably half that would work fine, but I've started setting mine at 8 "just to be sure".

And 4 Gb sounds like WAY too much.  From my experience, I almost never touch swap, and have never seen it go over 300 Mb (this on an old iBook with only 320 Mb RAM at the time)...so, maybe a Gb if you like "just in case" scenarios.

Finally, take anything I just said with a grain of salt.  Only been on Ubuntu since late 7.04 (not much linux experience prior either), and most of that's been through a GUI too...so no old school command line guru here by any means.

Good luck.

---

### Post by stream303 on 2008-11-12
Just be mindful that sunbird is running Intel and you are running ppc, which have differing partition requirements.  Although I do agree that swap probably doesn't need to be that big - I'll leave it up to the Intel guys for more specifics...

---

### Post by sunbird on 2008-11-12
Thanks for the tips. Unfortunately, I just read [this post]("http://ubuntuforums.org/showthread.php?t=976298&highlight=partition+size"), so it seems I can't have a shared home directory across two distros due to differences in the .pref directories. I could symlink the Documents/Pictures/etc., but I'm not sure it's worth it. I may just get rid of the OSX install and keep 8.04 for a bit longer. I want to wait a bit for a few more of the bugs to get worked out before jumping to 8.10.

---

