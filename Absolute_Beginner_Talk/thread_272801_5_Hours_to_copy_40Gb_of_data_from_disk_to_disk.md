---
title: "5 Hours to copy 40Gb of data from disk to disk"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-10-07
Do you think its reasonable that it should take 5 hours to copy 8647 of MP3 files (40Gb) from 1 disk to another on the same desktop? Am copying from RAID to non raid and I think there is something wrong with the way RAID0 has been setup. Even the other OS doesn't take this long.
Any ideas?

---

### Post by PWill on 2006-10-07
Hm...
5 hours for 40GB sounds a little much, but not unreasonable. What kind of transfer was this? IDE or SATA?

---

### Post by DOD1951 on 2006-10-07
Its aall IDE although the RAID is on PDC20276 (MBFastTrak133 Lite) which is kind of funny come to think of it. Maybe too lite :D

---

### Post by JayTee on 2006-10-07
If you're copying TO the RAID drive(s) and the RAID array is running RAID 5 then there will be more write latency as it has to calculate parity info "on the fly" and that makes the throughput slower than a standard IDE to IDE file copy. It's not a huge difference and usually would only matter on a server running SQL with a huge transaction load but it will be slower than a standard copy from drive to drive. Your transfers of 40GB over 5 hours average out to roughly 133 MB per minute which isn't that bad.

---

### Post by DOD1951 on 2006-10-07
Thanks for the explantion JayTee. This is from RAID0 to IDE. Maybe it does just take that long. I was thinking that there was a problem with the RAID0 as it also takes about 100 hours to update GTKPod local library from the RAID0 based MP3 files. So I gave up on GTKpod.

---

### Post by gn2 on 2006-10-07
You'ld perhaps be faster with USB2?

My 26Gb of Mp3's usually takes 45-55 minutes to move this way.

---

### Post by DOD1951 on 2006-10-07
I haven't even got as far as updating my Ipod yet! :) Haven't found anything to do that with, that actually works :( . This is more about file access/read/write etc on RAID 0.

---

### Post by CatKiller on 2006-10-07
Have you got DMA turned on for your drives?

---

### Post by TooDamFast on 2006-10-07
I had the same issue,  I had etc/fstab 2nd hard drive set to r rw (i cant remember what else) but I changed it to "default" and it fix it.

---

### Post by DOD1951 on 2006-10-07
> **CatKiller said:**
> Have you got DMA turned on for your drives?
I think that this may be where the problem is. The RAID0 is software raid via PDC20276 (MBFastTrak133 Lite) so the RAID0 disks look like they are just one big folder rather than being treated like a drive in the same way as had1 and hdb1. HDA1 (WinXP) and HDB1 (Filesystem)show up on the desktop as disks so when you click on the ICON it opens up to the files. For the RAID0 the disk shows up as 111.8 GB Volume and when I click on that ICON I get "Unable to mount selected volume error: device /dev/hde1 is not removable

error: could not execute pmount. Screenshot shows the RAID on devmapper and Screenshot1 shows the icons on the desktop that I am rambling on about.

---

