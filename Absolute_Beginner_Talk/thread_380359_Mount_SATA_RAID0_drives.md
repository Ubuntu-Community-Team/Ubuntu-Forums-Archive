---
title: "Mount SATA RAID0 drives"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-03-09
I have a RAID0 set up on 2 SATA drives divided up into 3 partitions. I have Kubuntu Edgy installed on a IDE drive. I trying to set up a triple boot system XP/Vista/Kubuntu. I found a great blog: [http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

I can't get Gparted, or Qparted for that matter, to read my RAID drives without giving me an error message. How can I mount RAID partition 1 as /media/XP and RAID partition 2 as /media/Vista?:confused:

---

### Post by overdrank on 2007-03-09
> **pilot550 said:**
> I have a RAID0 set up on 2 SATA drives divided up into 3 partitions. I have Kubuntu Edgy installed on a IDE drive. I trying to set up a triple boot system XP/Vista/Kubuntu. I found a great blog: [http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

I can't get Gparted, or Qparted for that matter, to read my RAID drives without giving me an error message. How can I mount RAID partition 1 as /media/XP and RAID partition 2 as /media/Vista?:confused:

Hi this is the best link I have found so far on sata raid. Hope it helps good luck!
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by pilot550 on 2007-03-09
Thanks. I'll check it out.

---

### Post by asonofmre on 2007-03-09
hello, this is my first post so be nice :)
I have a similar problem that i need some help with, I have XP and Ubuntu on my ide drive but have 2 sata drives in a riad) config, I have partition the raid drive in windows so that 200GB is NTFS and 40GB is in FAT32 as I have heard that linux can read and write to fat32 but not so easily to NTFS so I thought it would be a good idea to use this space to store any files that I might want to share between the 2 OS systems, however Ubuntu doesn't read the raid config (but can see each individual sata hard disk when installing)
I followed the link to the fake raid download, but am not sure which one to download, and once I do download is there a particular way to install programs into different versions of linux ie source code and rpms have caused me some confusion so far....
Thanks for any help:guitar:

---

