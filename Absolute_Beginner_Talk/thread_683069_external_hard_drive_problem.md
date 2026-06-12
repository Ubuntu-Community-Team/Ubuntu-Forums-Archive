---
title: "external hard drive problem"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-01-30
Hi
I am having trouble getting my external hard drive to mount. Sometimes it works other times not, even though its technically 'on'. Othertimes it dosen't show up on linux at all. I have looked at a couple of other topics about it, but i got confused, could someone explain what to do REALLY simply :)

---

### Post by ugm6hr on 2008-01-30
> **Falc7 said:**
> Hi
I am having trouble getting my external hard drive to mount. Sometimes it works other times not, even though its technically 'on'. Othertimes it dosen't show up on linux at all. I have looked at a couple of other topics about it, but i got confused, could someone explain what to do REALLY simply :)

Presumably it is a USB drive?

Does it have an external power supply, or does it draw power from USB port?

What settings do you have in the System-> Preferences-> Removable Drives and Media screen (Storage tab)?

Intermittent problems are bizarre though.  The only problem I have seen is with devices that take power from USB, which on some laptops can take up to 1 minute to mount.

---

### Post by Falc7 on 2008-01-31
yep it is usb, it has an external power source. its a seagate freeagent 500gb

my settings are:
mount removable drives when hotplugged
mount removeable media when inserted
browse removable media when inserted
thats all.

It is very much hit and miss. For example, just now i have plugged it in, i can hear is whirring quietly, and the orange light along the side is on. But ubuntu dosen't pick it up

---

### Post by ugm6hr on 2008-02-01
> **Falc7 said:**
> It is very much hit and miss. For example, just now i have plugged it in, i can hear is whirring quietly, and the orange light along the side is on. But ubuntu dosen't pick it up

Can't explain that one.

Does it appear in "My Computer" or in /media, even when not auto-mounted?  If so - maybe the auto-mount facility is a bit buggy?  I don't use it, so I wouldn't know.  Anyone?

---

### Post by jan quark on 2008-02-01
back to the roots
plugin your external hard drive
and run the following in the terminal and post the results please

```
mount
```

```
sudo fdisk -l
```

```
ls /dev/disk/by-uuid -alh
```

---

### Post by Falc7 on 2008-02-01
1.
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


2.
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

3.
total 0
drwxr-xr-x 2 root root 140 2008-02-02 02:51 .
drwxr-xr-x 6 root root 120 2008-02-02 01:54 ..
lrwxrwxrwx 1 root root  10 2008-02-02 01:54 08607f13-efe2-4177-bd62-6e0e13775eac -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-02-02 01:54 2C88743C8874071C -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-02-02 01:54 6CC6B1D6C6B1A0AE -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-02 02:51 BCA41749A4170594 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-02-02 01:54 fda1ddb9-59a8-48d9-818a-f34e21bc2ea1 -> ../../sda5

---

### Post by Bartender on 2008-02-01
Falc -
That's 

```
sudo fdisk -l
```

In other words, sudo fdisk -"ell", not sudo fdisk -"one"

Easy to make that mistake

---

### Post by Falc7 on 2008-02-02
oh yeah, didn't notice, here it is

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x452f1e71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9305    74738258    7  HPFS/NTFS
/dev/sda2           18596       19457     6924015    7  HPFS/NTFS
/dev/sda3            9306       18211    71537445   83  Linux
/dev/sda4           18212       18595     3084480    5  Extended
/dev/sda5           18212       18595     3084448+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

---

### Post by jan quark on 2008-02-02
This creates a directory "data" in /media (mount point is /media/data) and mounts your removable device there.

pmount is used to mount removable devices

```
pmount /dev/sdb data
```

To unmount the removable device 

```
pumount data
```

perhaps this will work

---

### Post by Falc7 on 2008-02-06
I install pmount using the terminal, then typed in the command, but nothing happened :(

---

