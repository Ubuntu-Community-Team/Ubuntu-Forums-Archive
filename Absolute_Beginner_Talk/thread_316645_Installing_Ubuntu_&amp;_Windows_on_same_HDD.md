---
title: "Installing Ubuntu &amp; Windows on same HDD"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Obi-Wan on 2006-12-11
I currently have a Sony laptop with a 30GB HDD. I'm extremely interested in installing both Ubuntu and WinXP on the same HDD. Right now WinXP is the only OS on this drive. 
1. Can I install both OS's on the same HDD without any major headaches or would a different version be better suited for this? I have Debian but I am a real virgin at the Linux end of things. I have been doing nothing but MS since getting involved in computers in 1998.
2. Would I have to reformat the HDD to get this done?
3. Do you know of any major issues I will run across?

---

### Post by MarkRobert on 2006-12-11
Pretty much ideal for it. Have a look at [this]("http://www.psychocats.net/ubuntu/partitioning").

---

### Post by beefcurry on 2006-12-11
There should be no Major issues if its just involving one harddisk. You DONT need to reformat your disk, with Acronis partition manager or anything similar partition your disk into two bits, one windows one black for ubuntu later. When installing ubuntu (from live CD) it would display gparted (somthing like partition magic) and you can create your linux parition there for your ubuntu. After that GRUB should automatically detect your windows OS and set everything up. When you boot again there should be a GRUB boot screen asking which OS to choose everytime.

---

### Post by DagMan on 2006-12-11
Laptops often times have the Windows partition and an additional hidden partition for other functions.  It isn't necisarrily just a matter of resizing the partition but also considering where the hidden partition is, if there is one, and where it needs to be as Windows views it after partitioning again.

If you see that there is a small partition on the drive, and it's the first partition on the drive, then it should be fine to just resize the Windows partition.  I've had trouble when it was at the end of the drive though, and it required resizing and moving data.

---

### Post by beefcurry on 2006-12-11
> **DagMan said:**
> Laptops often times have the Windows partition and an additional hidden partition for other functions.  It isn't necisarrily just a matter of resizing the partition but also considering where the hidden partition is, if there is one, and where it needs to be as Windows views it after partitioning again.

He uses a Sony Laptop which normally don't have hidden partitions. Also Windows itself does not create hidden partitions so if you've set everything up yourself its fine. Hidden Partitions SHOULD show up on somthing like Gparted or Acronis Paritition. Note: IBM computers normally include hidden partitions for backup, but its safe to delete them if you dont need them.

---

### Post by smoker on 2006-12-11
is is also wise to cleanse your windows of junk and unused applications, then defrag. this makes it simpler for the partition to be resized.

also, it is better to backup any important data, just as a precaution

---

### Post by Obi-Wan on 2006-12-12
Sorry for being so new, but if I install with a fat32 shared data would I still be able to play Win98 games that won't play on XP? I love Commandos and Duke Nukem but...

---

### Post by beefcurry on 2006-12-12
No you won't, but there is a chance that it will play in Linux under wine.

---

