---
title: "FAT32 for &quot;/&quot;"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by bdsatish on 2007-08-22
Hi,

Can i use FAT32 for "/"  (root) partition ? 

If yes, will I see the sub-directories, say, /home, /bin, etc. as normal Windows folders (assuming dual-boot) ?

---

### Post by PartisanEntity on 2007-08-22
As far as I know, FAT32 does not support permissions. Not sure that would work and definitely not a good idea to have a / without permissions.

---

### Post by LaRoza on 2007-08-22
If you want to be able to share with Windows, make a new partition with FAT32, and keep NTFS for Windows and EXT3 for Linux.

---

### Post by insane_alien on 2007-08-22
use ext3 and install the ext3 driver for windows. much better choice than the hideousness that is FAT32. it may have been fine in the early 90's but it is long past it now.

---

### Post by bdsatish on 2007-08-22
Well....

My default Win XP install is on FAT32 itself ! So all of my 80 GB is in FAT32 already.

Hence i thought, if ubuntu's "/" (root) were also FAT32, it'll be easy for me ;)

---

### Post by Outrunner on 2007-08-22
> **bdsatish said:**
> Hence i thought, if ubuntu's "/" (root) were also FAT32, it'll be easy for me ;)

Having the root partition on a FAT32 filesystem seems the complete opposite of 'easy' to me. You wouldn't run Windows on an ext3 partition, now, would you? ;)

---

### Post by bdsatish on 2007-08-22
Ohh.. great , i wudn't put WinXP on ext3 for sure !

So, it means, here's my final break-up:

#partition5        logical     21.0GB FAT32   /media/sda5

I'll split-up partition5 as :

15 GB      for  "/"        in   ext3
2 GB      for "swap"  
rest of GB    for "/home" in ext3

Does that sound OK?

---

### Post by igknighted on 2007-08-22
> **bdsatish said:**
> Ohh.. great , i wudn't put WinXP on ext3 for sure !

So, it means, here's my final break-up:

#partition5        logical     21.0GB FAT32   /media/sda5

I'll split-up partition5 as :

15 GB      for  "/"        in   ext3
2 GB      for "swap"  
rest of GB    for "/home" in ext3

Does that sound OK?

Looks good.  You know, there is a driver for windows to read ext3/ext2 drives.  It gives each partition its own drive letter (so you might have hard drives c:/ (windows), d:/ (/), and e:/ (/home).  I wouldn't mount / from windows unless you have to either.

Given the choice, I would much rather run windows on ext3 than FAT32 or NTFS... it's just a better filesystem.

---

### Post by kellemes on 2007-08-22
There is a lot to be said about partition-schemes..
But your setup is fine to start with.. You can always change your scheme when you want to.

---

### Post by bdsatish on 2007-08-22
One final ques..

Will the above scheme work with windows XP dual-boot?

Win XP is completely sitting in 20 GB primary partiton#1

I'm installing ubuntu on partition#5 (logical)...

---

### Post by igknighted on 2007-08-22
> **bdsatish said:**
> One final ques..

Will the above scheme work with windows XP dual-boot?

Win XP is completely sitting in 20 GB primary partiton#1

I'm installing ubuntu on partition#5 (logical)...

Err... looking at it closer... do you realize that your /home partition will only be 4gb?  This should usually be your LARGEST partition, as all your personal data/music/movies etc. get stored here.  The OS itself is usually fine on less than 10gb.  Also, why 2gb for swap?  Is this a laptop and how much ram do you have?

---

### Post by jnorthr on 2007-08-22
asked the same question myself and the answer came back as not a good idea. Better to keep the fat32 partition as windows until you get used to ubuntu. Just defrag your windows partition and make copies of your important data before playing with partitions. make root a ext3 format - not sure you have a choice for root.

---

### Post by bdsatish on 2007-08-22
It's a desktop with 512MB RAM... May be i'll reduce the swap then..

This is wat i thought:

Anyways, "/" will create "/home" directory by default.

I externally create "/home" of 4GB... So its like i have two "/home"s and i can share my apps between them

---

### Post by kelvin spratt on 2007-08-22
you do know you can convert fat32 to ntfs with your windows disc or someone elses with out loosing data, then just use ntfs3g this is a much better setup, as their can be lots of problems trying to read and write with windows to ext 3, linux has no such problems with writing to ntfs using ntfs 3g and no file size restrictions make it a winning combo, also you can change to ntfs
using windows editer but i do not know the codes as its a long while since i did it,.then use a 1gb ext2 swap, ext3 /root, ext3 /home, min. ive never seen any use on my swap partition with 1gb of ram

---

### Post by igknighted on 2007-08-22
> **bdsatish said:**
> It's a desktop with 512MB RAM... May be i'll reduce the swap then..

This is wat i thought:

Anyways, "/" will create "/home" directory by default.

I externally create "/home" of 4GB... So its like i have two "/home"s and i can share my apps between them

no, / will not have a /home if you create an external one.  It will mount the external one at the location /home (drives in linux are not mounted at the top level like windows, they can be mounted as any folder anywhere in the / filesystem (do be careful with this...).  Typically internal hard drives get mounted to /mnt/<name> and external storage (cd/dvd drives, usb drives, etc.) get mounted to /media.  If you want, it is also perfectly acceptable to mount your windows drive in /home/username/windows for easier access.  This is all easily done by setting the mountpoint in the installer, or if you do not wish to do it then, you can add a couple lines to the /etc/fstab file using the following guidelines (taken from the [Gentoo handbook]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8"), which you can view for more info or for some examples):

```
What is fstab?

Under Linux, all partitions used by the system must be listed in /etc/fstab. This file contains the mount points of those partitions (where they are seen in the file system structure), how they should be mounted and with what special options (automatically or not, whether users can mount them or not, etc.) 

Creating /etc/fstab

/etc/fstab uses a special syntax. Every line consists of six fields, separated by whitespace (space(s), tabs or a mixture). Each field has its own meaning: 
The first field shows the partition described (the path to the device file) 
The second field shows the mount point at which the partition should be mounted 
The third field shows the filesystem used by the partition 
The fourth field shows the mount options used by mount when it wants to mount the partition. As every filesystem has its own mount options, you are encouraged to read the mount man page (man mount) for a full listing. Multiple mount options are comma-separated. 
The fifth field is used by dump to determine if the partition needs to be dumped or not. You can generally leave this as 0 (zero). 
The sixth field is used by fsck to determine the order in which filesystems should be checked if the system wasn't shut down properly. The root filesystem should have 1 while the rest should have 2 (or 0 if a filesystem check isn't necessary).
```

---

### Post by 3rdalbum on 2007-08-22
I'm guessing that since you've only got 512 megabytes of RAM in your computer, that you're not planning on doing 3D animation or lots of video editing.

If that's the case, you can happily get by with 512 megabytes of swap. Use the extra 1.5 gigs on your / or your /home.

I'm not entirely sure what you mean by sharing programs across two /homes - if you could clarify this, we might be able to help you better. Programs don't get installed into /home, they get installed into /usr/bin so all users can access them. Since this is your first time out with Ubuntu, maybe you should consider having one partition for / and one for swap?

---

