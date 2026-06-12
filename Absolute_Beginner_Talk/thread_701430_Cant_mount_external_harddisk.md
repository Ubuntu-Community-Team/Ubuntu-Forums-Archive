---
title: "Cant mount external harddisk"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Oigy on 2008-02-19
When I put my external harddisk in the USB device a box appears asking me to force it or add it in sda1/media ,

1. I cant cant force it without accessing root (Don't wanna do that.) ?!
2. The sda1 "directory" is not a directory its a file.

what do i do . Just wanna mount my damn external harddisk.

---

### Post by PmDematagoda on 2008-02-19
Post the outputs of:-
```
cat /etc/mtab
```
and
```
sudo fdisk -l
```

---

### Post by Oigy on 2008-02-19
nicolai@Nicolais:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0


Sudo command: 
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefd5efd5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11784    94654948+  83  Linux
/dev/hda2           11785       12161     3028252+   5  Extended
/dev/hda5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

---

### Post by PmDematagoda on 2008-02-19
Try and mount the drive manually by doing the following:-

1) Create a directory in /media called "force":-
```
sudo mkdir /media/force
```

2) Mount the drive in the new mount point using:-
```
sudo ntfs-3g /dev/sda1 /media/force
```

If there aren't any errors received then go to the /media/force directory and see if your hard drive is mounted. If there are any errors received then post them here.

---

### Post by Oigy on 2008-02-19
Thn it does this:

/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/force -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/force ntfs-3g defaults,force 0 0

---

### Post by PmDematagoda on 2008-02-19
Do as the error message suggested and do:-
```
sudo ntfs-3g /dev/sda1 /media/force -o force
```
after that is done, go to the /media/force folder and check if the drive has been mounted.

---

### Post by Oigy on 2008-02-19
ye. now it works . thanks.

so i have to run that command evry time now . ?

---

### Post by KCormier on 2008-02-19
> mount -t ntfs-3g /dev/sda1 /media/force -o force
to mount once

> Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/force ntfs-3g defaults,force 0 0
Follow these directions to get it to mount every time.

open up xterm (alt + f2, then run "xterm")
run "sudo gedit /etc/fstab" and add the line above to the file.

also, when you're in xp, make sure you safely remove hardware before unplugging/shutting down the drive.  In linux, make sure you unmount it.  It should automount without even editing the fstab file as long as the filesystem is properly unmounted every time!

---

