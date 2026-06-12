---
title: "Getting XP to boot in GRUB"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Doormat on 2008-01-27
I have tried a number of things to get Grub to boot XP and haven't had any luck so perhaps you guys can help me out. Here is my situation:

I installed XP after Ubuntu so I had to install GRUB. I installed GRUB to the MBR (perhaps this was a mistake?).

I have a 5GB FAT32 partition as the first partition. Ubuntu 7.10 is installed on the 2nd partition. Swap should be the 3rd partition and I believe XP is the 4th partition. I have a number of partitions after this but I don't believe they are relevant.

I have tried adding XP to menu.lst and haven't had any luck. What should I add to menu.lst? Is there any other file I should edit?

---

### Post by Bachstelze on 2008-01-27
Please run *sudo fdisk -l* in a terminal and paste the output, as well as the contents of your /boot/grub/menu.lst.

---

### Post by Doormat on 2008-01-27
fdisk -l output:
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x164900b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      775221   390711352+   7  HPFS/NTFS
Warning: ignoring extra data in partition table 5

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x160241b5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         622     4996183+   b  W95 FAT32
/dev/hda2             623        1867    10000462+  83  Linux
/dev/hda3   *        1868        1991      996030   82  Linux swap / Solaris
/dev/hda4            1992       24321   179365725    f  W95 Ext'd (LBA)
/dev/hda5            1992       16489   116455153+   7  HPFS/NTFS

Disk /dev/sdb: 513 MB, 513802240 bytes
16 heads, 32 sectors/track, 1960 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x4fb94fb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1960      501744    e  W95 FAT16 (LBA)
```

menu.lst (I recently updated grub so its back to a default setting):
```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e9a4cd18-405b-4dcf-b306-54a6b292735f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9a4cd18-405b-4dcf-b306-54a6b292735f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9a4cd18-405b-4dcf-b306-54a6b292735f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Bachstelze on 2008-01-27
You have two NTFS partitions, which one is it that XP is installed on ?

---

### Post by Doormat on 2008-01-27
should be:
/dev/hda5            1992       16489   116455153+   7  HPFS/NTFS

---

### Post by Bachstelze on 2008-01-27
Okay, try to add that to your GRUB config file :

```
title           Windows XP
rootnoverify    (hd0,4)
makeactive
chainloader +1
```

---

### Post by Doormat on 2008-01-27
I received the following error when trying to run it from the grub menu:

```
Error 12: Invalid Device Requested
```

---

### Post by Bachstelze on 2008-01-27
Please paste the contents of /boot/grub/device.map.

---

### Post by Doormat on 2008-01-27
```
(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb
```

---

### Post by Bachstelze on 2008-01-27
Bad news there, your XP is installed on a Logical partition, so GRUB cannot boot it. You'll have to reinstall it on a Primary partition.

---

