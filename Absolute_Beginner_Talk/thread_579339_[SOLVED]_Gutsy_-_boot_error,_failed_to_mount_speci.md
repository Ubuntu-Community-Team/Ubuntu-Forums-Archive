---
title: "[SOLVED] Gutsy - boot error, failed to mount special device, /dev/hda3 does not exist"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-18
Just got gutsy upgrade last night.

grub looks like this
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=25b61946-bda3-4a9c-8627-b7030986be78 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=25b61946-bda3-4a9c-8627-b7030986be78 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=25b61946-bda3-4a9c-8627-b7030986be78 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=25b61946-bda3-4a9c-8627-b7030986be78 ro single
initrd		/boot/initrd.img-2.6.20-16-generic
```

Booting with kernel 2.6.22-14 causes an error fails to mount special device /dev/hda3 does not exist.  However if I select kernel 2.6.20-16 it mounts local file system ie /dev/hda3 and boots ok

---

### Post by tdrusk on 2007-10-18
Did you try the recovery mode?

---

### Post by vambo on 2007-10-18
Have a look at your /etc/fstab. If the entry for that drive is /dev/hda3 then you'll have to change it to UUID=
Seems as if the new kernel doesn't recognise the old way of doing things anymore ( which is daft IMO)

To get the UUID of your drives, run

```
sudo blkid
```

---

### Post by philinux on 2007-10-18
Cheers for prompt replies. I used recovery mode to find the errors.

The latest kernel uses "mount special device" to try to mount /dev/hda3 which is my home partition.

The older gutsy kernel uses "mount local file systems"

Strange that this should cause such a fatal flaw, it will affect loads of people.
this
Back to the problem - did this

```
sudo blkid
[sudo] password for philcb:
/dev/hdb1: UUID="0B5C-1AFA" TYPE="vfat" 
/dev/hda3: UUID="0f7689c1-b451-4bc8-9120-d5b224921210" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda1: UUID="25b61946-bda3-4a9c-8627-b7030986be78" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="a90e5447-5c12-48a3-ae2d-81cc81f53d58" 

```

not sure how to use it though having a poke around in fstab

---

### Post by philinux on 2007-10-18
fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=25b61946-bda3-4a9c-8627-b7030986be78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a90e5447-5c12-48a3-ae2d-81cc81f53d58 none            swap    sw              0       0
/dev/hda3 /home ext3 nodev,nosuid 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by vambo on 2007-10-18
> **philinux said:**
> fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=25b61946-bda3-4a9c-8627-b7030986be78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a90e5447-5c12-48a3-ae2d-81cc81f53d58 none            swap    sw              0       0
/dev/hda3 /home ext3 nodev,nosuid 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Right. See the entry for your /dev/hda5? It's just a comment. Beneath is the UUID entry
Do the same for your /dev/hda3 entry. That should be that.

---

### Post by philinux on 2007-10-18
Right ok - what options do I put right after the uuid?

---

### Post by vambo on 2007-10-18
Just exactly as they are - ie, the entries after the current /dev/hda3

---

### Post by philinux on 2007-10-18
New fstab worked just fine - cheers vambo - does anybody up there :rolleyes: know about this I wonder? 


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=25b61946-bda3-4a9c-8627-b7030986be78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a90e5447-5c12-48a3-ae2d-81cc81f53d58 none            swap    sw              0       0
# /dev/hda3
UUID=0f7689c1-b451-4bc8-9120-d5b224921210 /home ext3 nodev,nosuid 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

