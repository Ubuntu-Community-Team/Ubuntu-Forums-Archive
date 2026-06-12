---
title: "[SOLVED] Mp3 Player"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Wolfan on 2008-03-15
Hello there,

I'm having a problem with my MP3 player.  When I plug it in, nothing happens, I have tried manually mounting from sda2 on up to 5/6 (since my 2nd hard drive is on sda1) and nothing is there.  I'm to understand that simply plugging it in is supposed to work as that's the way that my flash drives and my USB HD work.  Is there a step I'm missing?

---

### Post by vanadium on 2008-03-15
To see whether your mp3 player is recognized as a disk, plug it in, open a command prompt and type

sudo fdisk -l

To see wether it is mounted (probably not), type

mount

Post these commands here, then we can tell what the output means, and show you how you can try to mount it manually: doing so might throw an error message that can give a hint about what is wrong.

It is also a good idea to give type and brand of your player. Some players do not behave as a hotplugable disk and have to be used differently.

---

### Post by schiznik on 2008-03-15
it will be sdbX, rather than sdaX - the a and b refer to different devices, and the numbers are the partitions on the devices.

try mounting /dev/sdb1

---

### Post by Wolfan on 2008-03-15
> **vanadium said:**
> To see whether your mp3 player is recognized as a disk, plug it in, open a command prompt and type

sudo fdisk -l

To see wether it is mounted (probably not), type

mount

Post these commands here, then we can tell what the output means, and show you how you can try to mount it manually: doing so might throw an error message that can give a hint about what is wrong.

It is also a good idea to give type and brand of your player. Some players do not behave as a hotplugable disk and have to be used differently.

I see, alright well here are the results of those two commands, the player is a GPX MW3337.
```

vinnie@vinnie-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1019 MB, 1019478016 bytes
8 heads, 32 sectors/track, 7778 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7778      995568    b  W95 FAT32

vinnie@vinnie-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
vinnie@vinnie-laptop:~$ 
```

schiznik, thank you for explaining that, this is what happened when I tried your instructions
```

vinnie@vinnie-laptop:~$ mount /dev/sdb1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

```

---

### Post by vanadium on 2008-03-16
Unproper mounting can be due to the filesystem being damaged. To see wether the file system is OK, you can run

dosfsck /dev/sdb1

(this is the equivalent to msdos "chkdsk a:)

To repair, you can use

dosfsck -a /dev/sdb1

(this is equivalent to msdos "chkdsk /f a:")

If indeed there was an error and it has been repaired, try unplugging and plugging back in: chances are now it will appear on the desktop. If it doesn't, then try mounting it manually to see the error during mounting.Run the following two commands, and post the output here

mkdir temp
sudo mount /dev/sdb1 temp

This makes an empty directory that we use as mount point, and the second command mounts the partition of your mp3 player in that directory. If mounting fails, an error will be thrown that can hint on the cause of the problem.

---

### Post by Wolfan on 2008-03-16
Thanks very much for all of your help.  That works. :-D

---

