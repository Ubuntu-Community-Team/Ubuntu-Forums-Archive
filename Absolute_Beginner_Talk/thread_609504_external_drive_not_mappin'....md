---
title: "external drive not mappin'..."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-11
Title says it all there...

I got an 80G seagate in an external USB enclosure, with linux file formatting.

 At first, it mapped, sort of. It showed half a G available space, with only 8G's worth of files on it :confused:(should have showed 72G available, right?). I deleted the files, and got still no available disk space.

I booted windows, it mapped the same way - as a disk with a couple of G's data on it. I formatted, and only a couple of G's got formatted fat32.

In windows disk manager, I deleted all partitions (3), and am now formatting all 80G's in NTFS (fat32 formatting not available for RAWdisk).

What do I have to do to get Ubuntu to map it, as available disk space?

---

### Post by The Tronyx on 2007-11-11
> **buccaneere said:**
> Title says it all there...

I got an 80G seagate in an external USB enclosure, with linux file formatting.

 At first, it mapped, sort of. It showed half a G available space, with only 8G's worth of files on it :confused:(should have showed 72G available, right?). I deleted the files, and got still no available disk space.

I booted windows, it mapped the same way - as a disk with a couple of G's data on it. I formatted, and only a couple of G's got formatted fat32.

In windows disk manager, I deleted all partitions (3), and am now formatting all 80G's in NTFS (fat32 formatting not available for RAWdisk).

What do I have to do to get Ubuntu to map it, as available disk space?

In a terminal, type:
> 
sudo fdisk -l


Please post the results here.

---

### Post by ellis rowell on 2007-11-11
I use an 80GB HDD which I partitioned into three drives, it's fat32 and has always worked perfectly under Windows and Linux. I cannot understand why you are unable to format as fat32 under Windows (I used XP, are you using Vista and is this another Vista problem?). I can only suggest that you get someone else to format it as fat32 if you cannot.

---

### Post by The Tronyx on 2007-11-11
> **ellis rowell said:**
> I use an 80GB HDD which I partitioned into three drives, it's fat32 and has always worked perfectly under Windows and Linux. I cannot understand why you are unable to format as fat32 under Windows (I used XP, are you using Vista and is this another Vista problem?). I can only suggest that you get someone else to format it as fat32 if you cannot.

If I am reading this correctly, it's not that he can't format it, but that he cannot get it to mount/map.

---

### Post by buccaneere on 2007-11-11
> **2point0 said:**
> In a terminal, type:


Please post the results here.


I just found this info to mount, 2.0... I think I got that now (the HDD is formatting NTFS now in windows very slowly).

Yes, I'm doing the NTFS from a Vista boot there, ellis.

Will I be able to mount the NTFS-formatted blank USB HDD, when booted back into Ubuntu???

If not, what will I need to do?

If so, what is the proper dismount procedure, to make sure that files copied to the external drive are saved?

I'm at the parents, offloading vids from a dvr, and need to ascertain file copy before deleting from dvr...

Thanks!

---

### Post by buccaneere on 2007-11-11
> **2point0 said:**
> If I am reading this correctly, it's not that he can't format it, but that he cannot get it to mount/map.

It WAS 'auto'-mounting, but not showing full HDD capacity...

---

### Post by The Tronyx on 2007-11-11
> **buccaneere said:**
> It WAS 'auto'-mounting, but not showing full HDD capacity...

Did it show different partitions, i.e. HDB1 20g HDB2 30g, etc?

---

### Post by buccaneere on 2007-11-11
> **2point0 said:**
> Did it show different partitions, i.e. HDB1 20g HDB2 30g, etc?

Yes, it did show partitions...

---

