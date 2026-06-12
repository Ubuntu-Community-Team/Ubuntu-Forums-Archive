---
title: "mount problems"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-02-09
Hi.

Can anyone help out? I am using Kubuntu amd I am trying to set up nautilus as the main file manager. I have managed to set  up the file associations an the folders now open in nautilus but now when I connect my removable HDD, I get an error:

"media dev/sdc1 is a folder but a file was expected"

Anyone know how I can rectify this?

cheers
niteblind

---

### Post by taurus on 2007-02-09
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by niteblind on 2007-02-09
here is the output i should mention this was done with my phone connected but it gives the same error as the HDD.

As the phone is detected i get a pop up asking me what i want to do. It is when i select the option to open in a new window that I get the error come up. Whne i click OK to the error i see a boz that has source written in it and a progres bar which does not move at all.

I should also say that this only happens at the point where kubuntu tries open the devices for me. If i double click the icon on the desktop then the media is loaded in a new nautilus window without the error.

cheers in adbance

Wolverine:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          66      530113+  82  Linux swap / Solaris
/dev/sda2              67        1647    12699382+  83  Linux
/dev/sda3   *        1648        7295    45367560    b  W95 FAT32

Disk /dev/sdb: 86 MB, 86016000 bytes
3 heads, 18 sectors/track, 3111 cylinders
Units = cylinders of 54 * 512 = 27648 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2723       73492+   4  FAT16 <32M

Disk /dev/sdc: 956 MB, 956238336 bytes
64 heads, 32 sectors/track, 911 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         912      933826+   6  FAT16

---

