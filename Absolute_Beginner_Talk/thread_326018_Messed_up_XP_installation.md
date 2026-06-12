---
title: "Messed up XP installation"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by milkaa on 2006-12-26
Hi 

I had dual-boot XP-Ubuntu on 2 separate hdds. My XP started acting up and I decided to do fresh re-installation.  Since I'm at it, I thought I'll do a re-installation of my Ubuntu as well. 

Here's what I did:

1) Popped in my WinXP CD.
2) Deleted my Ubuntu partition A.
3) Deleted my WinXP partition B.
4) Formated and Re-installed my WinXP on B.

My XP installation went fine.. but when I logged in to XP, I realised that it was a much scaled down version of XP. Just a blue screen with the recycle bin by the side. Start-up menu does not even have Internet Explorer. 

What did I do wrong?

I searched around and realised I should have used the "fixmbr" command first to settle some booting issue. Can I still do that now?

Anyways, I went on to install Ubuntu back on A and I'm running that now. Just need to fix my XP.

Appreciate all help. Thanks!

---

### Post by Duck2006 on 2006-12-26
what is the output of 

fdisk -i

---

### Post by milkaa on 2006-12-26
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4159    33407136    7  HPFS/NTFS
/dev/sda2            4160       19456   122873152+   f  W95 Ext'd (LBA)
/dev/sda5            4160        9258    40957686    7  HPFS/NTFS
/dev/sda6            9259       14357    40957686    7  HPFS/NTFS
/dev/sda7           14358       19456    40957686    7  HPFS/NTFS

Disk /dev/hda: 13.5 GB, 13578485760 bytes
255 heads, 63 sectors/track, 1650 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1579    12683286   83  Linux
/dev/hda2            1580        1650      570307+   5  Extended
/dev/hda5            1580        1650      570276   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4997    40138371    7  HPFS/NTFS

---

### Post by Duck2006 on 2006-12-28
What does your men.lst look like

it sounds like windows didn't fully install

---

### Post by jvc26 on 2006-12-28
Quite possibly the solution is to delete your XP partition again, reformat it NTFS/FAT32(If you want to access it from the ubuntu partition) and reinstall, looks like an incomplete install. Can you live without it or is it vital?
Il

---

### Post by oilchangeguy on 2006-12-28
did you use a restore disk or a disk with only windows on it? the restore disk will set it up just like the day you bought it. the windows only disk only gives you the default desktop (sky and hill) and the recycle bin in the lower right hand corner. to change this right click on the desktop, arrange icons, auto arrange. close. now right click the desktop again select properties. select desktop, customize, then add the icons for my computer, my documents, internet explorer, etc.

---

