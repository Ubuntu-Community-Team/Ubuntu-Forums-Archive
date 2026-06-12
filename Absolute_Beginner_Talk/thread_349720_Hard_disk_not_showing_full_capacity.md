---
title: "Hard disk not showing full capacity"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by abacate on 2007-01-30
I just salvaged a 120GB Seagate hard disk from my old Win98SE box. It was working like a dream there but now that I plugged it into my new computer and tried it out on ubuntu I can only see it as a 31.50GB drive. The same thing occurred on my friend's WinXP and my BIOS also shows it as around 33 000MB. It is not jumpered to work as a smaller drive and should be connected properly. 

The HD is a Seagate Barracuda ST3120022A, last formatted as a fat32 drive for use with Win98SE. It's been quite a long time since I used the old computer and even longer since I installed the HD in it but I think I had to tweak something with Seagate's DiscWizard. Unfortunately I was unable to find a linux version of that software.

Also tips on how I should go about reformatting the drive once I have it running as it should are welcomed.

---

### Post by Duppy on 2007-01-30
Erm, do you want a dual boot? 

OR just Ubuntu on the HD?

Use the liveCD to log onto Ubuntu, then use the partitioner in there to delete all the partitions and make a fresh new one.

---

### Post by mangoti on 2007-01-30
I believe fat32 cannot be over 32Go. Try another file system or 4 fat32 partitions of 30Go each.

---

### Post by dexter on 2007-01-30
I believe the problem in this case might be your BIOS. Older BIOS's can't handle disk greater then 32 GB. How old is this computer ? You can try updating the BIOS if there's an update for it.

---

### Post by abacate on 2007-01-30
Well up until a couple of weeks ago I'd been dual booting with WinXP but then my XP broke down and I'm not sure if I'll reinstall it in a while. The computer I'm using now is around two and a half years old and was originally built with a 200gig S-ATA HD also by Seagate (ST3200822AS) which I have to run through a raid system.

---

### Post by louieb on 2007-01-30
After you installed it did you check the BIOS settings?
In BIOS you should be able to set detection to auto and mode to LBA.
Did you use fdisk to find the drive size? The drive may have space that is not allocated to a partition. The total size of the drive is listed near the top of the output. 
```
sudo fdisk -l
```that a lowercase l as in little.
I don't think its a BIOS limit, and you said the capacity limiting jumper  was not used.  I have one computer that has the 30 gig limit and it just flat refuses to boot if a drive larger than 30 gig  is installed.

---

### Post by abacate on 2007-01-31
> **louieb said:**
> After you installed it did you check the BIOS settings?
In BIOS you should be able to set detection to auto and mode to LBA.
Did you use fdisk to find the drive size? The drive may have space that is not allocated to a partition.

The BIOS settings should be ok. This is what I got from fdisk:

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1312    10538608+   7  HPFS/NTFS
/dev/sda2            1313       24320   184811760    f  W95 Ext'd (LBA)
/dev/sda5            1313       19593   146842101    7  HPFS/NTFS
/dev/sda6           19594       20900    10498446    b  W95 FAT32
/dev/sda7           20901       21683     6289416   83  Linux
/dev/sda8           21684       21749      530113+  82  Linux swap / Solaris
/dev/sda9           21750       24320    20651526   83  Linux

Disk /dev/hdb: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table

```

First shown is of course my main HD with XP and Ubuntu installations. Interestingly enough fdisk seems to report the problematic HD as slightly bigger than Disks Manager or WinXP.

---

