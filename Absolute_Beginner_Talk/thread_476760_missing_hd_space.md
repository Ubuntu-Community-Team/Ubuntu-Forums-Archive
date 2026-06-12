---
title: "missing hd space"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by thermophile on 2007-06-17
I dual booted my pc last year and (as I see now) put in some bizzarr partitions. as follows

hda1 - ntfs - 46.48 GB (windows boot)
hda4 - ext3 - 51.17GB (linux boot)
hda2 - est3 - 97.65GB
hda3 -extended
   hda5 - fat32 - 35.56gb
   hda6 - linux swap - 2.01gb

my linux boot (hda4) is full but I can only find 13-14gb worth of data on it.  the trash is empty and I can't think of anything else to do to try to find that missing 35gb.  I have a 250gb external hd so I was thinking of wiping hda2-6 and reinstalling linux but that seems pretty extreme.  I don't have all of the windows program disks with me so I don't want to wipe hda1.  

am I about to use a nuke against a flea sized problem?  or does wiping most of the hd seem like a good course of action?

thanks

---

### Post by logos34 on 2007-06-17
what's the output for
**df -h**
?
What about
**du -sh /var/cache/apt/archives**

shows how much space packages are taking up

Is hda4 inside the extended partition?

**sudo fdisk -lu**

---

### Post by thermophile on 2007-06-17
> **logos34 said:**
> what's the output for
**df -h**
?
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              51G   48G  188M 100% /
varrun                506M  124K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile


What about
**du -sh /var/cache/apt/archives**

477M    /var/cache/apt/archives

shows how much space packages are taking up

Is hda4 inside the extended partition?

no hda5 and hda6 are in the extended partition

**sudo fdisk -lu**


Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    97482419    48741178+   7  HPFS/NTFS
/dev/hda2       204796620   409593239   102398310   83  Linux
/dev/hda3       409593240   488392064    39399412+   f  W95 Ext'd (LBA)
/dev/hda4        97482420   204796619    53657100   83  Linux
/dev/hda5       409593366   484166969    37286802    b  W95 FAT32
/dev/hda6       484167033   488392064     2112516   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by logos34 on 2007-06-17
sure it's not all that porn you downloaded and squirreled away in some /.hidden folder? you'd be surprised how fast that stuff piles up...  ;-)

Seriously, you could try doing a filesystem check from the live cd (partition has to be unmounted) to see if there are any anomalies
[B]
sudo fsck /dev/hda4[/B]

---

### Post by thermophile on 2007-06-17
do you mean that I should boot from the live cd then run fsck?

---

### Post by logos34 on 2007-06-17
Yes.

---

### Post by thermophile on 2007-06-17
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda4: clean, 113115/6717440 files, 12695621/13414275 blocks

---

### Post by thermophile on 2007-06-17
even checked that all my hidden porn was included int the files that I'm seeing.  guess that's not the problem, hee hee

this is really starting to annoy me.  is there anything else I should try?

---

### Post by logos34 on 2007-06-17
I've been googling around and not coming up with much...about the only other cause of such a problem I can think of would be say if you had daily cron jobs set to do automated full backups and they were just being appended to some folder (instead of overwriting previous one), piling up, eating up gigabytes upon gigabytes of disk space.  

dh will report '100%' even when it is really only like 90% full because it reserves a percentage as buffer, but that's not even close to your problem...

---

### Post by thermophile on 2007-06-17
I just back things up as I think of it.  nothing scheduled

What kind of problems am i looking at if I do wipe hda2-6 and reinstall?  how likely is that to cause a problem in my windows partition?

---

### Post by logos34 on 2007-06-17
> What kind of problems am i looking at if I do wipe hda2-6 and reinstall? how likely is that to cause a problem in my windows partition?

as long as you don't touch it/resize it, shouldn't have a prob.

---

### Post by thermophile on 2007-06-17
thanks

---

### Post by pmg on 2007-06-18
Try running **sudo du -k / | sort -nr | less** .  It will take a while.  Because of the sort it won't display anything until it's scanned everything, but when it's done it will show each dir on the system in order of size, including all the subdirs under it, so of course it will show / first.  You could umount any other filesystems to take them "out of view", but it looks like the other filesystems you've got don't have much in them.  If you haven't used **less** before, to get you started: "space" pages down, **u** pages up, and **q** quits.  

This should help you narrow down what subdirs have all the data in them.

---

