---
title: "USB WD hard drive is RW only by root ..."
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-03
I am using one of those mini USB hard drives -- the Western Digital 250GB.

I issue the following:

  sudo  mount  -t vfat  /dev/sdc1  /media/WD

... but only root can write to this hard drive.  Ordinary users can read but not write.

Is there a way to use the mount command to mount a device as r/w for everyone?

Thanks

Carl

---

### Post by vanadium on 2007-10-03
It is logical that the drive belongs to root if root mounts it. Anyway, for an external USB drive, you should not need to mount the drive using the terminal: it should automount. If it does not, then try pmount to mount the drive. This is designed to mount pluggable devices as normal user.

---

### Post by timcredible on 2007-10-03
if you let the system automount it for you, the user that's logged in gets write permissions to it.  if you need more users to access it, try the -o rw parameter.  also, if you want the drive to remember file permissions, make sure you re-format it as ext3 instead of fat32, fat32 doesn't support file permissions.

---

### Post by EarlGrey on 2008-04-16
I have the same problem, also WD passpor drive. It does aoutmonout, but it is not writable (tome as logged user).

Please do you have any suggestions? Thanks alot!

---

### Post by kpkeerthi on 2008-04-16
> **EarlGrey said:**
> I have the same problem, also WD passpor drive. It does aoutmonout, but it is not writable (tome as logged user).

Please do you have any suggestions? Thanks alot!

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by EarlGrey on 2008-04-16
Thanks for your quick reply, however, it is a USB drive that I formated to ext3. Before, when the FS was FAT, it was all ok.

If you have any suggestions, I would be very grateful.

---

### Post by kpkeerthi on 2008-04-16
Plugin your USB drive and post the output of ```
sudo fdisk -l
```.

* I suggest you start a new thread for your problem.

---

### Post by EarlGrey on 2008-04-20
Thanks! Now I made two partitions. (sdc) so the second one is ext2 now. However, this problem occurs even if the external disk is formated whole as ext2.

Thanks for any help!

```

martin@vavrousek:~$ sudo fdisk -l
[sudo] password for martin:

Disk /dev/hdb: 120,0 GB, 120*034*123*776 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 14*593
Jednotky = cylindry po*16065 * 512 = 8*225*280 bajtech
Identifikátor disku:&#8239;0xbccd45db

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/hdb1   *           1       14216   114189988+  83  Linux
/dev/hdb2           14217       14593     3028252+   5  Rozší&#345;ený
/dev/hdb5           14217       14593     3028221   82  Linux swap/Solaris

Disk /dev/sda: 250,0 GB, 250*059*350*016 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 30*401
Jednotky = cylindry po*16065 * 512 = 8*225*280 bajtech
Identifikátor disku:&#8239;0x000b4fd8

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Rozší&#345;ený
/dev/sda5           30025       30401     3028221   82  Linux swap/Solaris

Disk /dev/sdc: 160,0 GB, 160*041*885*696 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 19*457
Jednotky = cylindry po*16065 * 512 = 8*225*280 bajtech
Identifikátor disku:&#8239;0x5b6ac646

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sdc1               1       10196    81899338+   b  W95 FAT32
/dev/sdc2           10197       19457    74388982+  83  Linux

```

---

