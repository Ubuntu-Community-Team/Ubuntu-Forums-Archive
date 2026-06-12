---
title: "need XP back!"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by sam510 on 2007-09-18
Alright this is my 5th post and still no resolution. I installed ubuntu last saturday and i liked it, Only problem was that it wouldnt support the games i played so i decided to boot back into xp. When i try boot it it just hangs in the Starting up.... Ive also tried 5 diffrent boot loaders to try to boot xp, None was able to boot it. I know the grub loader is configured correctly, I just thing something happened to the partion. I tried every possible way to fix it, Even using the fixmbr cmd in windows repair. That just made it say disk read error so i restored grub. Please help i dont know what to do.

---

### Post by Clay_Banger on 2007-09-18
have u tried reinstalling xp over the old installation? it sounds like u have resized the partition, rendering winxp useless.

---

### Post by splintercellguy on 2007-09-18
Do you actually have an XP partition? For the games issue have you tried using Wine? The Gaming & Leisure section has a fascinating stickied guide to using it, along with the Wine AppDb? Have you tried using Super GRUB CD?

---

### Post by sam510 on 2007-09-18
Ive used cedega but My wow crashes like every 5 minutes, Also there is no other way I can restore my windows xp :( i really dont want to reinstall.

---

### Post by splintercellguy on 2007-09-18
Does the XP partition even exist? What is the output of sudo fdisk -l? And don't use Cedega, nasty payware :). This AppDb entry ([http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)) and a thread in Leisure & Gaming section should help you get WoW working. Be sure to use the latest Wine version by following these instructions: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by sam510 on 2007-09-18
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7829    62886411    7  HPFS/NTFS
/dev/hda2           10199       11851    13277722+   5  Extended
/dev/hda3           11852       24321   100165275   83  Linux
/dev/hda5           10199       11474    10243768+   7  HPFS/NTFS
/dev/hda6           11475       11851     3028221   82  Linux swap / Solaris

---

### Post by Baby Boy on 2007-09-18
Try using the [GAG]("http://gag.sourceforge.net/") disc to restore your WinXP.

---

