---
title: "Ubuntu with OS 9 and OS X - No root file system is defined"
date: 2009-08-31
forum: Apple Hardware Users
---

### Post by Chris Grk-O-Matic on 2009-08-31
1 Ghz Titanium Powerbook
 
 
This is according to what I learned so far:
 
   I've partitioned my hard drive in in this order using Disk Utility:
 
   Ubuntu - 4.7 gigs - Mac OS Extended format 
   OS 9 - 1.1 gigis - Mac OS Extended format 
   OS X - 87 gigs - Mac OS Extended format 
 
   I've already installed OS X and OS 9.
 
To launch Ubuntu off the cd image I use live-nosplash-powerpc but the confusion begins when I try to install it - mainly the 'Prepare disk space' part. I've read the threads and it looks like I have to manually specify the partitions. When I select the partition that I created for Ubuntu, it says, 'No root file system is defined.'
 
So what I gathered, or lack thereof, from the threads is that I have to do a swap, and a NewWorld boot partition, etc. Seems easy enough but it looks like I'm missing a few minor details in the process which is preventing me from successfully installing Ubuntu.
 
Can someone please provide step-by-step details to get me through the manual partition process? I hope I've setup everything up correctly thus far.
 
 
Kind Regards,
Chris

---

### Post by tiresia on 2009-08-31
You did it right, you need now just to delete with gparted (are you using the livecd or the alternate installer?) the partition you made for Ubuntu and then let the installer do the job for you choosing the 'automatic' installation (no manual partitioning).

Anyway, you should also know that 4GB is really quite small... If you want to work in Ubuntu you need at least 8-10GB, also because the installer will take some space for the swap partition

---

### Post by Chris Grk-O-Matic on 2009-08-31
Wooohooo it's installing!
 
Thanks a bunch for that information.
 
 
When in gparted the first 8 lines were:
 
/dev/hda1  !   unknown     31.50 KiB
/dev/hda2  !   unknown     28.00 KiB
 
... down to hda8
 
 
Is there something that should be done or is this normal?

---

