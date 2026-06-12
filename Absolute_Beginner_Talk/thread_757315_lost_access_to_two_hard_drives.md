---
title: "lost access to two hard drives"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by nobeta on 2008-04-16
I have searched for solutions and will post data that has been asked for in other postings. I had linux mint 3.1 on the 500 gb. drive and mounted some partitions and do not remember how I did it. gparted is showing 4 partitions locked. sdc2 and sdc5 on the 465 gb drive and sda3 and sda5 on the 372 gb drive. This unmounting thing may be causing the problems but I am not sure. The message on the smaller drive is "error loading operating system" and after format will not even let me install vista. On the bigger drive I get a message most of the time " failed to start the x server". I restored that drive from a acronis backup which has worked before, but the restore did not do anything this time, just get the same message. I do have backup on the external drive of the "x" thingy and a backup of the "root" but do not know how to make use of them. I did  a grub find and got (hd2,0) (hd4,0). I have run supergrub off a cd and ran the automatic and it did not do anything to help. I am on an ubuntu easy cd right now, but I don't think I can correct the locked partitions from here. gparted shows the partitions in the details section but the unmount command is grayed out and cannot be unlocked from there. While I am waiting I will reboot to a gparted boot disk and try to unlock from there. I have osx on the 80 gb drive but have not checked to see if it is working. I want to leave windoz pretty bad as I have spent 90% of my time the last few years just trying to make the thing secure. xp is working on the two raid 0 drives.  Here are the results of the three things I see asked for. 


ubuntu@ubuntu:~$ cat /etc/fstab

unionfs / unionfs rw 0 0

tmpfs /tmp tmpfs nosuid,nodev 0 0

/dev/sdc5 swap swap defaults 0 0

/dev/sde5 swap swap defaults 0 0

ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ cat /etc/mtab

proc /proc proc rw 0 0

sysfs /sys sysfs rw 0 0

tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0

tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0

varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0

varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0

udev /dev tmpfs rw,mode=0755 0 0

devshm /dev/shm tmpfs rw 0 0

devpts /dev/pts devpts rw,gid=5,mode=620 0 0

tmpfs /tmp tmpfs rw,nosuid,nodev 0 0

ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# fdisk -l



Disk /dev/sda: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x272e272d



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       60802   488392033+   7  HPFS/NTFS



Disk /dev/sdb: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00141b00



Disk /dev/sdb doesn't contain a valid partition table



Disk /dev/sdc: 500.1 GB, 500107862016 bytes

15 heads, 63 sectors/track, 1033622 cylinders

Units = cylinders of 945 * 512 = 483840 bytes

Disk identifier: 0x00065b27



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *           1      206686    97659103+  83  Linux

/dev/sdc2          206687     1033617   390724897+   5  Extended

/dev/sdc5          206687      216733     4747144+  82  Linux swap / Solaris

/dev/sdc6          216734     1033617   385977658+   7  HPFS/NTFS



Disk /dev/sdd: 750.1 GB, 750156374016 bytes

255 heads, 63 sectors/track, 91201 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xa4b57300



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1               1       91201   732572001    7  HPFS/NTFS



Disk /dev/sde: 400.0 GB, 400088457216 bytes

255 heads, 63 sectors/track, 48641 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00000001



   Device Boot      Start         End      Blocks   Id  System

/dev/sde1   *           1       19122   153597433+  83  Linux

/dev/sde2           19123       47884   231029760    7  HPFS/NTFS

/dev/sde3           47885       48641     6080602+   5  Extended

/dev/sde5           47885       48641     6080571   82  Linux swap / Solaris



Disk /dev/sdf: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x000cbb29



   Device Boot      Start         End      Blocks   Id  System

/dev/sdf1               1        4844    38909398+   b  W95 FAT32

/dev/sdf2   *        4845        9729    39238762+  af  Unknown

root@ubuntu:~# 


thanks

---

### Post by Diabolis on 2008-04-16
I'm not sure if understood fully your problem. if you can't un-mount partitions from gparted, do it manually like this:
```
umount *mount point*
```
example: umount /media/sda1

> " failed to start the x server"
This error show up when your xserver is not well configured, most of the times is due to a bad graphics card driver selection. You can fix it with this command:
```
sudo dpkg-reconfigure xserver-xorg
```.

---

### Post by nobeta on 2008-04-22
The big problem is loss of access to the two drives. IT just so happens that those two drives are showing locked partitions when running the partition editor within ubuntu easy cd. When I boot to the cd g parted it does not show those partitions locked. When I use the umount command within the easy cd ubuntu it says the partitions are already unmounted. I started having these massive problems with these two particular drives ( the 80 gb drive is booting into osx and the raid is booting into xp) when I forgot to unmount some drives I had mounted within linux and rebooted the system. At least that is my suspicion as that it was at the same time. i have made some progress with the drive that I restored mint from a acronis boot disk, but the 4 times that it did boot all the way into mint the mouse would not respond. Is it possible to have this massive amount of headaches because I forgot to unmount some partitions? I have tried numerous times to install vista on these drives and keep getting a message that windows is unable to find a system volume that meets its criteria for installation. partition magic gave me messages partition table error 110 found and 105 found. Spinrite even crapped out and said it had a division overflow error. I am trying to run a western digital diagnostics, having trouble with the cd, but this has happened to two drives at around the same time and it has to be something very recent, don't you agree? Thank you for your time and effort. 

nobeta

---

