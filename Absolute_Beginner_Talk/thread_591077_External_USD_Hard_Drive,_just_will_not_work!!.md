---
title: "External USD Hard Drive, just will not work!!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Bonnobo on 2007-10-25
HI there,
I am having a problem with my Seagate 320Gb external drive. Now I have recently installed upgraded to 7.10, but the drive was recognised on 6.10. my results from -mount are:-

warmdent@warmdent-desktop:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda5 on /media/NOEL type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma sk=077,usefree)


and from fdisk are:-

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb24281d

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 4660 37431418+ 83 Linux
/dev/hdc2 4661 4865 1646662+ 5 Extended
/dev/hdc5 4661 4865 1646631 82 Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x17a2a492

Device Boot Start End Blocks Id System
/dev/sda1 * 1 44718 22537840+ 7 HPFS/NTFS
/dev/sda2 44719 155061 55612872 f W95 Ext'd (LBA)
/dev/sda5 44719 99603 27662008+ b W95 FAT32
/dev/sda6 99604 155061 27950800+ b W95 FAT32

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

..where /dev/sda is my external drive.

From cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdc1
UUID=6944632d-3664-4115-aee2-abd17bb3f0ac / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc5
UUID=e67b70ce-8986-49f1-8d27-6252973b8816 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

sorry for the amount of code, but I haven't got any idea as to what to do. As I am a beginner, desperately trying to shake off Microsoft

Thanks for any help........

---

### Post by Bonnobo on 2007-10-25
Sorry the title should read USB, not USD...

---

### Post by Qwerty_ on 2007-10-25
Have you installed ntfs-config?

```
sudo apt-get install ntfs-config
```

Then run

```
sudo ntfs-config
```

Select your required options.

---

### Post by Double R on 2007-10-25
> **Qwerty_ said:**
> Have you installed ntfs-config?

```
sudo apt-get install ntfs-config
```

Then run

```
sudo ntfs-config
```

Select your required options.

This worked for my 500Gb Seagate. Thanks.
And just a note, I had to restart before getting it t work (ctrl + alt + backspace)

---

### Post by slibuntu on 2007-10-25
> **Bonnobo said:**
> 


Disk **/dev/sdf**: **320.0 GB**, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

**..where /dev/sda is my external drive.**

From cat /etc/fstab




It looks as though /dev/sdf is your external harddrive, given you said its 320GB, and its probably formatted as FAT-32 so the above post may not be much help, unfortunately i don't have a fix for it, but this will be a welcome bump!

---

### Post by Bonnobo on 2007-10-25
So are you saying it will work in a different format.  If so is there a way of changing this without losing any of the data already on the drive.  I don't want to use Ext 3 as this drive is also used in ........Windows.  Maybe I can use ntfs?

---

### Post by BRAiN8 on 2007-10-27
thats why u gotta go EURO. USD losing value :P.. hehe well not sure but think i got some tips. what error message do u get when you mount through the file manager? does it spit back what you pasted on the first paragraph?

anyhow.. u gotta treat the hard drive nice.. do u do the whole "Remove Hardware Safely" ordeal on windows?... (right click removable media icon on system tray) I know that ubuntu won't mount if you just "pulled" the plug... i guess it flags it to be "hot-swappable" or not when you remove the drive on windows. so try pluggin it in windows..mount it and remove safely and then try again..

or u can try force mount..not sure if its safe..? hehe

i know beginner tips..forgive me.

---

