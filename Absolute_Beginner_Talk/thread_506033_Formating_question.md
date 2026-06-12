---
title: "Formating question"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Cappy on 2007-07-21
I just bought a dual-core Toshiba A135-S4666 / A135-4666 laptop with Vista on it.
Vista is too slow even on a Core 2 Duo so I'm going to reformat it to XP / Ubuntu (already checked for compatibility, both work fine after some drivers).

If I install XP, to the first 15GB of the hard drive do I need a 50MB partition in front of it for GRUB to be mounted for Ubuntu's /boot or is that advice wrong?

I've heard you need to do that if Windows is bigger than 8.5GB and it is the front partition. Anyone have an experience with this?

Thanks =)

---

### Post by forestpixie on 2007-07-21
no that  advice is wrong Grub is just a file 

I've read that it's best to install XP first then Ubuntu,  - as to sizes depends on how much you have and how you want to use them.

---

### Post by Wim Sturkenboom on 2007-07-21
The proof:
```

wim@desktop1:~$ sudo fdisk -l
Password:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       26892   189791910    f  W95 Ext'd (LBA)
/dev/sda5            3265        7180    31455238+   7  HPFS/NTFS
/dev/sda6            7181       10444    26218048+   b  W95 FAT32
/dev/sda7           10445       13708    26218048+  83  Linux
/dev/sda8           13709       13838     1044193+  82  Linux swap / Solaris
/dev/sda9           13839       26892   104856223+  83  Linux
```This works; as you can see Linux starts somewhere at 80GB (sda1+sda5+sda6)

sda1 is windows, sda5 is for my documents (windows) and sda6 for sharing.
sda7 is ubuntu, sda8 is swap for linux and sda9 is /home (similar to documents and settings in windows)

---

### Post by dptxp on 2007-07-21
15 GB XP
next 10-15 GB / (root) ext3. (for small hard disk, keep 6-8 GB)
Rest minus 2 GB /home (ext3)
2 GB SWAP.
Install Windows first.
Do not worry about GRUB space

---

### Post by Cappy on 2007-07-21
Heh thanks! =)

---

### Post by Wim Sturkenboom on 2007-07-22
2GB swap is to (or is it too) much in my opinion. 2x memory size with a max of 1GB is the rule that I keep.

@dptxp
Why do you advice a seperate home partition for Linux and not for Windows :?

---

