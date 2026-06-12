---
title: "initial hard drive mount"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-05
how do I tell if my hard drive is mounted correctly, it never showed up on the desktop and where can I see how much free space I have?

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738       11896    49472167+  83  Linux
/dev/sda3           11897       12161     2128612+   5  Extended
/dev/sda5           11897       12161     2128581   82  Linux swap / Solaris

```Why do mine say sda and everyones' say hda, and no drives on the desktop?

---

### Post by zmuth734 on 2007-01-05
bump from pg 2

---

### Post by Famicommie on 2007-01-05
I'm not sure what you mean by your first question, but to check your disk space open up a terminal and type df

---

### Post by zmuth734 on 2007-01-05
> **Famicommie said:**
> I'm not sure what you mean by your first question, but to check your disk space open up a terminal and type df

People keep saying when its mounted correctly it shows up on your desktop.  The only thing that shows up for me is my cd-rom drive.

---

### Post by CroEragon on 2007-01-05
It doesn't have to show on desktop. Mine never showed and it is mounted properly. And if you didn't figure out about sda and hdd you see sda because you have Serial ATA(SATA) disc and hdd is for IDE discs. I have both and i have 2 SATA (sda1,sda2) and 2 IDE (hdd4,hdd5).

---

### Post by steve.horsley on 2007-01-05
the command **df -h** will tell you what's mounted and how much space it has. The command **mount** lists other information about mounted drives.

---

