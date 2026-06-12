---
title: "[SOLVED] Please Help Me- System Dead"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by damispyderbyte on 2008-02-25
Ok... windows crashes (again) and i'm writing this from a bootable linux disk. I am going to reinstall Windows but need my data. The disk has some weird error and i can't mount it.
This is what i get:

ubuntu@ubuntu:~$ sudo mount /dev/sda2
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
ubuntu@ubuntu:~$ 

It really Makes me mad.... :lolflag:

any sugestions?? Also i get this weird thing when i go to boot screen (witch does not load) i get the infinity symbol and thats it! WEIRD. I really need my data i got some work stuff.  I can't mount so i cannot even scan it for viruses. Also it is a sata drive and this CD would not even boot without the flag "irqpoll" 

I know you guys can help  Many Thx

Tyler

---

### Post by backinthecity on 2008-02-26
If i'm not mistaken the newer version of ubuntu it may be the beta right now i'm not exactly sure. They included a program that helps assist mounting NTFS harddrives. 

hope this helps slightly

---

### Post by oedha on 2008-02-26
you can't mount while the windows crached and lock the disk up
or can you post sudo fdisk -l ?
can you boot from windows boot cd.....
what kind of crash ?

---

### Post by damispyderbyte on 2008-02-26
What happened is windows was in the middle of updating and somereason shut off. It corroupted the disk and made it unreadable. I will post more when i get home.

Thx for responces

tyler

---

### Post by az on 2008-02-26
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

Use ddrescue to image the partition to another disk.

Then, try to force-mount the partition and read what you can off it.  If not, try to fix the filesystem.  If all else fails, data-carve the files you need off the image.


You can use ubuntu-rescue-remix to do all that:  [http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by damispyderbyte on 2008-02-26
How do i fix the file system??:confused:  I'm kinda new at this :) 

Tyler

---

### Post by az on 2008-02-26
> **damispyderbyte said:**
> How do i fix the file system??:confused:  I'm kinda new at this :) 

Tyler

Well, if the problem is hardware, you may still be able to get a perfect read after several tries.  After the image is made, you can write it back to the disk (or another disk) and then try to boot it.

Writing it back to your disk should cause the drive's error-sensing mechanism to reallocate the bad blocks to functioning ones.  I would not continue to use that drive, though.

If the filesystem is still in an inconsistent state, just booting into windows should make it check and fix itself.

If you truly can't boot it, try ntfsfix.

---

### Post by damispyderbyte on 2008-02-26
Thx I'll try that~!! :popcorn:

---

### Post by damispyderbyte on 2008-02-26
Anyone have a precompiled package for ntfsfix. I can't compile with a live cd.

Thx for help! 
](*,)

---

### Post by az on 2008-02-26
sudo apt-get install ntfsprogs

Or just use the rescue-remix.  It's already on it.

Do not try to fix the filesystem on the original disk without first making an image of it.

---

