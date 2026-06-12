---
title: "PVR and RAID"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by wruwtrix on 2007-11-08
I'm interested in creating a PVR (undecided on MythTV, SageTV, or Freevo), but have some questions on hard drive performance and setup.  I haven't used RAID before, but I'm more than willing to figure it out if it would improve performance on my theoretical system (3GHz P4, 2GB DDR2-533 RAM, 2 x 750GB SATA HDD, HD-PVR tuner if they are compatible with Linux before next Spring).

Is it worthwhile to use software RAID on a homebrew PVR?  Which RAID level should I (or can I) run in Gusty?

Thanks for your help

---

### Post by NT4usB on 2007-11-08
No... imo, There is little benefit to RAID on a pvr.
It's a waste of space to mirror and striping doesn't buy you anything since read/write is not that intense.
Only reasonable use would be to make one big volume out of a couple small drives.
Drives are so cheap though, save the small drives for the OS and get a big single for recordings.
I run two drives in mine. One for the os and the other for recordings. 
When I added the slave, I had two of the 120's striped for recordings. I've since added a single 500 for the recordings and use the array for other storage.

---

