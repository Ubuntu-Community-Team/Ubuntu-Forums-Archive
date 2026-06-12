---
title: "Startup manager problems"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Stang94 on 2007-07-08
Hi there all kinda new to the scene my question is I downloaded the program Startup Manager and did some changes on it everything was going fine till I changed a setting in it . Now my problem is that I am missing in grub my kernels grub starts and all but missing my kernel on ubuntu feisty . Not sure what to do only options I have is memtest or vista loader hate to have to reinstall again I have it set the way now that I like it . Thanks in advance for all the help

---

### Post by taurus on 2007-07-08
You need to boot from a LiveCD, mount the partition where / is (or /boot if you have one), edit /boot/grub/menu.lst, and see if you get an entry for a kernel on the GRUB menu now.

If you don't know how to mount your harddrive with the LiveCD, post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Stang94 on 2007-07-08
SO this is what I get out of the command that you had me run I also was able to mount the drives but I cant figure it out any ideas ??? Thanks again for the help      ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+   7  HPFS/NTFS
/dev/sda2            9727        9969     1951897+  82  Linux swap / Solaris
/dev/sda3            9970       19452    76172197+  83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36481   293033601    6  FAT16

Disk /dev/sdc: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7314    58748481    7  HPFS/NTFS
/dev/sdc2            7314        9730    19405824    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by taurus on 2007-07-08
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda3 /mnt/ubuntu
```
Then, post

```
cat /mnt/ubuntu/boot/grub/menu.lst
ls -la /mnt/ubuntu/boot
cat /mnt/ubuntu/etc/fstab
```
Or if you need to edit menu.lst, just do

```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by Stang94 on 2007-07-09
Hi there thanks for the help I got it fixed I found I had aback up menu list so I just copied the words from there onto grub and got it to work again thanks for your help all

---

