---
title: "Thumb Drive Recovery?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-03-15
Hey everyone,

Pretty urgent situation here.

My roommate has a thumb drive which is evidently corrupt.  He uses it with his Windows PC and it has valuable information on it.  I thought I would try it in Ubuntu, but I can't see it come up on the desktop when I plug it in.  Is there anything else I could try or any software that may help us here?

---

### Post by Josey on 2007-03-15
I only know of a windows version... iolo search and recover.

---

### Post by maxamillion on 2007-03-16
Is the thumb drive not even mounting or can you just not see the data?

If you just can't see the data, I have had 100% success recovering data off of thumb drives using [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") (part of the TestDisk package found in the repositories and can be installed via Synaptic, apt-get, or aptitude .... or Smart ... etc.)

I have only done it an a few USB drives, but it worked for me everytime (be sure to select the exact file extensions you want it to search for or else it will "recover" alot of garbage)

Hope this helps.

-Adam

---

### Post by brandoncolorado on 2007-03-16
> **maxamillion said:**
> Is the thumb drive not even mounting or can you just not see the data?

If you just can't see the data, I have had 100% success recovering data off of thumb drives using [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") (part of the TestDisk package found in the repositories and can be installed via Synaptic, apt-get, or aptitude .... or Smart ... etc.)

I have only done it an a few USB drives, but it worked for me everytime (be sure to select the exact file extensions you want it to search for or else it will "recover" alot of garbage)

Hope this helps.

-Adam

Thanks, going to give that a try.  Appreciate the responses guys!

---

### Post by mcduck on 2007-03-16
If you don't need to recover data, but just want to get the drive working again, first disable automounting of USB drives (in System/Preferences/Removable drives and Media), then plug the drive in and use fdisk, gparted or qtparted to remove all existing partitions from the drive, and then make a new one (using vfat file system).

---

### Post by brandoncolorado on 2007-03-18
> **mcduck said:**
> If you don't need to recover data, but just want to get the drive working again, first disable automounting of USB drives (in System/Preferences/Removable drives and Media), then plug the drive in and use fdisk, gparted or qtparted to remove all existing partitions from the drive, and then make a new one (using vfat file system).

Thanks,  I got the data off with a Windows demo program and then used this trick.

Problem resolved.  Appreciated.

---

### Post by p0g0 on 2007-03-23
> **brandoncolorado said:**
> Thanks,  I got the data off with a Windows demo program and then used this trick.

Problem resolved.  Appreciated.

What program did you use brandon?

---

### Post by brandoncolorado on 2007-03-23
> **p0g0 said:**
> What program did you use brandon?

EasyRecovery Professional

---

### Post by p0g0 on 2007-03-24
> **brandoncolorado said:**
> EasyRecovery Professional

Thanks man :) , I'll give it a try.

Update: It worked like a charm :).

---

