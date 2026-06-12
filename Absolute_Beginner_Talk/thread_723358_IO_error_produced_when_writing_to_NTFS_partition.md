---
title: "I/O error produced when writing to NTFS partition"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-13
It's kinda weird.  This is a new hard drive, so I doubt these errors are being produced by bad sectors.

For instance, I just created an empty folder on the drive with no problem.  But when I try to rename it, I got a I/O error (no further details are shown when this error appears).

I tried to move a folder containing a bunch of avi files, and it produced the same error.  But when I tell the computer to just copy the files (not the folder their contained in) to the NTFS partition, into the new folder I managed to create but can't rename, the files copy right over with no errors.

How should I go about troubleshooting this?

---

### Post by (((X))) on 2008-03-13
Read this
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

known issues are mentioned

---

### Post by reeseslover531 on 2008-03-13
also it is possible that the new drive is bad, certain sectrors could be dead on arrival

---

### Post by diablo75 on 2008-03-13
If it helps, this hard drive is an external USB drive, which I toss back and forth between Ubuntu and Windows running inside VMware.  On occasion, I've had to mount the drive in Windows and then do a proper removal of it before Ubuntu would auto-mount it upon next reboot, probably because of an "in use" flag being ticked by Windows....  I know the problem with this drive is something I did a long time ago... I can't remember what I did....

---

