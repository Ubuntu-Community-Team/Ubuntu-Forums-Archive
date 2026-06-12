---
title: "reformat my 2nd HDD"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by eric magray on 2007-01-22
hi i have a second hard drive i need to reformat to ext3 or fat32, im sure theres a way to do it from the command line. could someone help me?

---

### Post by taurus on 2007-01-22
```
sudo mke2fs -j /dev/hdb1
```
(Better make sure it's /dev/hdb1 though.)

---

### Post by eric magray on 2007-01-22
thank you very much, i havent tried it yet but thank you

---

### Post by eric magray on 2007-01-22
no it didnt work im not sure what it did but i used sudo fdisk -ls to check it after and it was still ntfs system

---

### Post by taurus on 2007-01-22
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by eric magray on 2007-01-22
Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1256    10088788+   7  HPFS/NTFS

---

### Post by taurus on 2007-01-22
No wonder it didn't work.  It's /dev/hdc1, not /dev/hdb1.  Told you to make sure it was /dev/hdb1...  Is /dev/hdc1 mounted at all?

```
sudo umount /dev/hdc1
sudo mke2fs -j /dev/hdc1
sudo fdisk -l
```

---

### Post by eric magray on 2007-01-22
i did make sure it was hdc1 i just didnt know i needed to unmount it

i try it with the new code

---

### Post by eric magray on 2007-01-22
i got this when i entered all of your code and it seemed way too quick to reformat the whole drive
> eric@eric-desktop:~$ sudo umount /dev/hdc1
umount: /dev/hdc1: not mounted
eric@eric-desktop:~$ sudo umount /dev/hdc1 /media/windows
umount: /dev/hdc1: not mounted
umount: /media/windows: not mounted
eric@eric-desktop:~$ sudo mke2fs -j /dev/hdc1
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
1261568 inodes, 2522197 blocks
126109 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2583691264
77 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 36 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
eric@eric-desktop:~$ sudo fdisk -l

Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1192     9574708+  83  Linux
/dev/hda2            1193        1247      441787+   5  Extended
/dev/hda5            1193        1247      441756   82  Linux swap / Solaris

Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1256    10088788+   7  HPFS/NTFS

still ntfs                                                                                    ^^

---

### Post by taurus on 2007-01-22
Reboot and run that command again.

```
sudo fdisk -l
```

---

### Post by eric magray on 2007-01-22
i rebooted and then did the fdisk and got this again

> eric@eric-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1192     9574708+  83  Linux
/dev/hda2            1193        1247      441787+   5  Extended
/dev/hda5            1193        1247      441756   82  Linux swap / Solaris

Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1256    10088788+   7  HPFS/NTFS


im gonna cry

---

### Post by eric magray on 2007-01-22
could someone at least point me to a guide that would help me

its an ntfs drive mounted on /dev/hdc1

---

### Post by taurus on 2007-01-22
Install gparted and see if you can use it to convert it to ext3.

```
sudo aptitude update
sudo aptitude install gparted
```
It will be in System -> Administration.

---

### Post by eric magray on 2007-01-23
thanks for the tip. i installed qtparted instead, but it worked great.

---

