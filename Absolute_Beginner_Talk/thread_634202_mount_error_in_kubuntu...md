---
title: "mount error in kubuntu.."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-07
**SEAGATE HAS ISSUES, I DID NOT MARK THIS THREAD AS SOLVED  ;)**

I tried to mount my 500 GB seagate drive and I got this error:

```
hal-storage-removable-mount-all-options refused uid 1000
```

Would appreciate your help  :D     :popcorn:  <winner gets the prize

sv

---

### Post by taurus on 2007-12-07
Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by staticvoid on 2007-12-07
**sudo fdisk -l**
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5827c934

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4864     1494045    5  Extended
/dev/sda5            4679        4864     1494013+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```

ok, so it sees it, but it is NTFS. Do I need to get ntfs-config or something? How would I mount it manuelly? I can't see it on the desktop or in the /media folder or in the place konquer says are the external drives


when I plug it in the device lights up. it mounts in windows...

sv

---

### Post by hotweiss on 2007-12-07
just restart Windows with that drive attached twice.... that will fix the journaling issue that is most likely taking place... happened to me to

---

### Post by staticvoid on 2007-12-07
yeah, i've tried that multiple times...

I'll try it again though!  :D maybe on a dif computer?

its a funny seagate drive that you can't unplug untill the comp is shut off or something bad could happen (some people report data loss or even a screw up drive)

sv

hope its an easy fix :D

---

### Post by szaka on 2007-12-07
> **staticvoid said:**
> its a funny seagate drive that you can't unplug untill the comp is shut off or something bad could happen (some people report data loss or even a screw up drive)

Actually not some people, but unfortunately quite many :-( An article was just published about it in one of the bigger computer magazins today: [http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux](http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux)

Here is a quote:
*"Rose Allen from Seagate Tech support said that work-round may succeed, but there is no way that she, or her band will support that sort of thing"*

---

### Post by staticvoid on 2007-12-08
wow.


shucks.

[I]

The problem is to do with the power-saving systems on Seagate's latest range of drives and the fact that it is shipped already formatted to NTFS.
The NTFS is only a slight hurdle to Linux users who have a kernel with NTFS writing enabled or can work mkfs. But the "power saving" timer is a real bugger. 
It will shut shut the drive off after several minutes of inactivity and helpfully drop the USB connection. When the connection does come back it returns as USB1 which is apparently as useful as a chocolate teapot.
As our reader points out this is a, "fairly **** idea perfectly implemented, " unfortunately while Windows can handle it, Linux and Mac's can't cope.
There are a few work-arounds but Seagate Tech Support says they do not know what they are. Instead they are telling man plus dog that their latest drives do not support Linux.[/I]

---

