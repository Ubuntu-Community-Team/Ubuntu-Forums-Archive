---
title: "Problems with GRUB after clean install."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by SpiceWeasel on 2006-09-26
I'm having some trouble getting GRUB to register my master SATA drive that has windows xp on it and i'm not sure why since i recently ran DBAN on my hard drives then installed windows on the SATA and Ubuntu on an ATA drive.

here is what ive tryed so far starting with my sudo fdisk output

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       18935   152095356   83  Linux
/dev/hda2           18936       19457     4192965   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

```

Then i went into the menu.lst and entered the following

```
title Microsoft Windows XP Professional
rootnoverify (hd2,0)
savedefault
makeactive
map         (hd0) (hd2)
map         (hd2) (hd0)
chainloader +5
```

I used +5 because when i had everything dual booting before, that flashed by as grub booted windows.

Does anyone see any problems with this?

---

### Post by mitch.c on 2006-09-26
> **SpiceWeasel said:**
> ```
title Microsoft Windows XP Professional
rootnoverify (hd2,0)
savedefault
makeactive
map         (hd0) (hd2)
map         (hd2) (hd0)
chainloader +5
```

I used +5 because when i had everything dual booting before, that flashed by as grub booted windows.

Does anyone see any problems with this?

Have you tried chainloader +1?

---

### Post by SpiceWeasel on 2006-09-26
yup and the response i get from that is NTLDR not found. I had that problem after installing windows before linux at one point, both on the same hard drives i have them on now. I really dont know where im going wrong as i had windows and ubuntu dual booting perfectly before doing the same type of instal.

---

### Post by mitch.c on 2006-09-26
> **SpiceWeasel said:**
> yup and the response i get from that is NTLDR not found. I had that problem after installing windows before linux at one point, both on the same hard drives i have them on now. I really dont know where im going wrong as i had windows and ubuntu dual booting perfectly before doing the same type of instal.
NTLDR not found is a Windows error... If you got that far, grub was configured correctly. Your problem is most likely boot.ini on the window partition. Boot into linux and mount your ntfs partion, post the contents of boot.ini.

---

### Post by SpiceWeasel on 2006-09-27
I was having some trouble with the MBR on the SATA so i used windows recovery console for windows (the thought of windows messing with the MBR scared me but it needed to be done). Then i reinstalled windows (it actauly advised me to after fixing the MBR) on there with the other drives unplugged and when i plugged them back in and editted the grub menu and now im dual booting again. Thanks for the suggestions guys.

---

