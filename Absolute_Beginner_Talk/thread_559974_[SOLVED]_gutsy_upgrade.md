---
title: "[SOLVED] gutsy upgrade"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-25
Question: when gutsy is released, I plan on using it. Based on my hard drive partitions, do I have to re-format hda3,4,5, or do I just use the live cd and "install". hd1,2 is used for Win Xp (I dual boot) for now.
This is my HD
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 490 4137 29302560 7 HPFS/NTFS
/dev/hda2 1 489 3927861 b W95 FAT32
/dev/hda3 4138 9565 43600410 83 Linux
/dev/hda4 9566 9729 1317330 5 Extended
/dev/hda5 9566 9729 1317298+ 82 Linux swap / Solaris
__________________
Ubuntu: definite proof that life can exist without M$ Windows...

---

### Post by wolfen69 on 2007-09-25
just install as normal and choose your linux partition.(hda3)

---

### Post by ramjet_1953 on 2007-09-25
It may be a good idea to back-up your /home directory and then copy it back into your new install.

This will save all of your current preferences, emails, contacts, etc.

Regards,
Roger 8)

---

### Post by Jimmyfj on 2007-09-25
A clean install will always be the best due to possibility of download errors during an upgrade. Possible download errors and connection speed is one thing to consider before an upgrade. I've seen upgrades that took six hours to complete even from a fast internet connection on a 1 GH computer with more than enough memory installed, 512 MB.

Anyway. Be sure to backup critical user files  before upgrading/installing.

---

### Post by nikoPSK on 2007-09-26
You don't actually need to download a cd. Just type <Alt>+F2 then

```
gksu “update-manager -c -d”
```

It will find then install gutsy over your current ( )buntu package. I did it and it worked fine.:)

---

### Post by nikoPSK on 2007-09-26
whoopsie. Mabye the cd needs to be in the drive. Iunno. When I did it mine was. :confused::popcorn:

---

