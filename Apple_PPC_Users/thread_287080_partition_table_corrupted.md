---
title: "partition table corrupted"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by seatea on 2006-10-28
I have messed up the partition scheme on my  hard drive with Disk Utility  under Mac OS X. According  to gpart, I have erased my root partition and reformatted it  to an "unknown" filesystem. Fortunately, my /home partion is still ok. I am thankful now that I  had put them on separate partitions, although the problem  that  occurred could have just  as easily  trashed my /home partition.

I had a partion  that  was 1 GB that  I planned  to use  to transfer files between Linux and Mac OS X. I had formated  it fat32 under Linux, but  Mac OS X wouldn't mount it. I tried to fromat it under OS X to fat32 thinking the Mac OS Disk Utlity would make it  accessible to the  Mac system, but could not do that. I then thought of trying to format it as Mac unix and mounting it under Linus somehow. What happened when I  tried to restart from my hard disk was that the root file could not  be found. I started up off my external drive and found that my originl partition table had completely  changed. /dev/hda15 was my original root, but now the root  partition looks like it is /dev/hda13 under gparted. Also, the filesytem  is not  recognized as ext3. Oddly, under  Disk Utlity in Mac OS X, the partition numbering system has changed  from what it was too, but /dev/hda13 is /dev/hda11! 

I am wondering if I can (1)  restore the  original partition table, (2) use  my curent partiton  table and restore the root partition for ubuntu, or  should I (3)just scrap the whole drive and redo everything? Mac OS X and Mac OS 9 are still completely functional, but their partition numbers have changed from the original setup. Option (3) probably is  the most  correct thing to do. It  baffles me  that the  partition table keeps changing  from restart to restart.

---

