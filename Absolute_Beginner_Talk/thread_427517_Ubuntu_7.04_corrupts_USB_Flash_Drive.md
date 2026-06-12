---
title: "Ubuntu 7.04 corrupts USB Flash Drive"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by brainmaps on 2007-04-29
I'm not sure if this is the right place to post this, but my SanDisk 1 Gb USB Flash Drive was apparently corrupted by writing to it from Ubuntu.   The drive works fine in Ubuntu but I can no longer read/write to it from Win XP SP2.   Anyone have any ideas why this happened?

I'm now paranoid about hooking any external HDD's up to Ubuntu for fear that it will corrupt everything.

---

### Post by nixclusive on 2007-04-29
Did you do anything like formatting the drive in Ubuntu? By default that would place an ext2/ext3 filesystem on it which is not readable in Windows. At least not without some help from an external program. Try mounting the drive in Ubuntu and enter this in the terminal:```
mount 
```This should give you a list of all the mounted filesystems along with some addidional information. Check what filesystem your drive is having in the list. You may need to re-format that drive in FAT filesystem for use in Windows.

---

### Post by brainmaps on 2007-04-29
thanks for the quick reply.  The result of mount is:
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf=8,umask=077)

I didn't format the flash drive on Ubuntu.  All I did was copied some files off of it (which I had done previously without any issues), and the new thing was, I created a test file on the flash drive because I was curious if I could write to it from Ubuntu.   To my knowledge, it was writing to the USB flash drive that corrupted it.  Subsequently trying to view the USB flash drive in Win XP SP2 gave me an input/output error and would not allow me to read or write to the flash drive.   I could not even reformat the flash drive in Win XP.

I have external HDD's in NTFS format that have 600 GB to over a TB of data and am concerned about trying to hook these up to Ubuntu for fear of corruption, which would be a catastrophe in this case.  Is this fear warranted?

---

### Post by ronocdh on 2007-04-29
> **brainmaps said:**
> thanks for the quick reply.  The result of mount is:
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf=8,umask=077)

I didn't format the flash drive on Ubuntu.  All I did was copied some files off of it (which I had done previously without any issues), and the new thing was, I created a test file on the flash drive because I was curious if I could write to it from Ubuntu.   To my knowledge, it was writing to the USB flash drive that corrupted it.  Subsequently trying to view the USB flash drive in Win XP SP2 gave me an input/output error and would not allow me to read or write to the flash drive.   I could not even reformat the flash drive in Win XP.

I have external HDD's in NTFS format that have 600 GB to over a TB of data and am concerned about trying to hook these up to Ubuntu for fear of corruption, which would be a catastrophe in this case.  Is this fear warranted?
Many people are accustomed to the fact that they can insert and yank out flash drives with abandon in Windows XP; in *nix operating systems, it is far safer and more reliable to manually "eject" the drive with a command before physically disconnecting it. I know I hear of this adjustment issue a lot when I see people switching to OS X on Macs.

I have seen improperly removed drives exhibit similar symptoms. Could this explain your case?

---

### Post by brainmaps on 2007-04-29
yes, this could definitely explain it!  I omitted mentioning this because I had a hard time believing initially that yanking the drive without ejecting could be the problem.  This is going to be a hard habit to overcome.   Any ideas on how to reformat the drive so that it is read/write on XP again?  I am unable to reformat the drive in XP and so will have to do it in Ubuntu.

---

### Post by Incompetnce on 2007-05-03
i have a similar problem;

my flash drive works fine with windows (except one folder is corrupted)
in ubuntu it has decided my drive is read only. and when i unmount it, the light does not turn off.
i now want to reformat my drive and see if it will work properly. could someone explain how please?

---

### Post by legolas on 2007-05-04
> **Incompetnce said:**
> i have a similar problem;

my flash drive works fine with windows (except one folder is corrupted)
in ubuntu it has decided my drive is read only. and when i unmount it, the light does not turn off.
i now want to reformat my drive and see if it will work properly. could someone explain how please?

Same thing here.  I just bought the new sony Pocket bit mini, a 1gig flash drive.  It says it is read only, most of the time.  The strange thing is, is that it did allow me to copy a file onto it one time, and then it complained that it was read-only from then on.    I have a WD passport, and external hard drive and she works fine.  Just that Sony flash is giving me problems.  Here is my mount results, and as you can see, they have the same settings, but very different results!  Any advice for us to try?  Thanks.

/dev/sda1 on /media/disk-1 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdb1 on /media/WD Passport type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

---

### Post by ciccio80 on 2007-07-25
Any news? I have the same problem...

---

### Post by Mornedhel on 2007-07-25
Just for the record. Some USB drives will * not * run under Linux, for reasons beyond my understanding. This happens. At my school we have computers running under WinXP and others under Fedora Core, and some exotic USB drives will refuse to work under FC4, while others will. If that's the case, you can always try and reformat the drive in FAT32 (after backing everything up, of course) and pray.

Side note : I actually had a similar situation happen to me this morning. Now, I always cleanly mount and unmount everything, but this particular time, the USB key (SanDisk 1GB) would not mount under Feisty Fawn (previous unmount under Linux was clean, last unmount was under WinXP and clean as well). I reformatted the drive in FAT32 under Windows and everything mounted fine afterwards.

---

### Post by ciccio80 on 2007-07-25
No, the problem is different. Everything was fine both in windows xp and ubuntu. But now (I suspect some corruption caused by Ubuntu) both in Windows and Ubuntu the key is mounted in read only mode and I can't format it.

Any ideas?

Thanks
Francesco

---

### Post by Mornedhel on 2007-07-25
How exactly did you unmount the drive last time ?

Linux works a bit differently than Windows for external drives, it puts more priority into other stuff it considers more important and delays writing to disks (even when the progress bar is at 100%, it is NOT safe, most of the time, to remove the drive). You really have to wait until the "It is now OK to remove your drive" popup appears (not the exact words).

I would say this provides about 98% of OS-caused external drive failures. It may also be possible that your drive is getting old...

---

### Post by ciccio80 on 2007-07-25
And in this case  is the drive unrecoverable or it is possible to restore it (i don't mind about the data)?

Thanks
Francesco

---

### Post by Mornedhel on 2007-07-25
If the corruption was caused by a forced unmount, it's possible (formatting it in the process, but I don't know how in this situation as you seem to have trouble doing it). If it's old, unless you know of a special time continuum warp device to make objects travel towards the past rather than the future...

---

