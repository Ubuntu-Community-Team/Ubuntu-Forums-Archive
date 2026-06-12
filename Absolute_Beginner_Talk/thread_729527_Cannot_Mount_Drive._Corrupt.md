---
title: "Cannot Mount Drive. Corrupt?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by cschoeps on 2008-03-19
Hi all,

I recently installed Vista on my computer for the use of a few programs. The other night I was streaming media from my external hard drive through vista to my Xbox 360. I lost power during this, and had some problems when I booted back up. Vista thinks the drive is corrupt. I can mount it, but when I try to access the folders, it tells me that it is corrupt and can't be read. I tried to restart into Ubuntu, but it is Unable to be mounted. Here is the error I get:

Unable to mount the volume 'SimpleDrive'.
$MFTMirr does not match #MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory. (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

I don't have any kind of raid on this drive, so I tried the first part, ran chkdsk /f and rebooted twice. This hasn't changed the problem at all. I've been sure to boot into windows and safely remove the hardware before rebooting, and this does not change anything. Ubuntu refuses to change. This is my media drive, and a lot of it would be a real pain to replace.

Any help would be greatly appreciated. Thanks!

---

### Post by cschoeps on 2008-03-20
Anyone have any ideas? Anyways, I'm using photorec to grab my pictures, and hopefully will find a similar program for my videos. Those are the only two corrupt folders.  I'll post to let people know how they work, in case anyone else has problems.

---

