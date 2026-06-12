---
title: "Can't Boot after moving Partitions!!!"
date: 2013-11-21
forum: Any Other OS
---

### Post by newberry-anthony on 2013-11-21
I installed Ubuntu, and was trying to move around and clean up some partitions, to delete my windows 8 partition and just leave Ubuntu, with my Windows 7 intact. After i moved some partitions, i now can't boot AT ALL on my hard drive. It used to be grub, now it just says Operating System Missing when i boot to my hard drive.

I have already attempted to fix it using a windows recovery disk, with bootsec.exe /fixboot and bootsec.exe /fixmbr  but neither one did anything for me. I have a program called TestDisk that i can use, but i need some help on going forth from here. The ONLY thing i care about saving is my windows 7 partition data, the rest is removable, but if it can stay, i'd prefer it to.

ANY help would be greatly appreciated, as i can only boot from a ubuntu live cd at this point!!!


Here is some "boot info" i got from a Boot Info Script i found on another forum.

```

============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 52430848. But according to the info from 
                       fdisk, sda3 starts at sector 307200000.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /etc/fstab

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1843152 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   287,668,223   287,666,176  83 Linux
/dev/sda2         287,668,224   307,199,999    19,531,776  82 Linux swap / Solaris
/dev/sda3         307,200,000   956,229,631   649,029,632   7 NTFS / exFAT / HPFS
/dev/sda4         956,231,678 1,465,147,391   508,915,714   f W95 Extended (LBA)
/dev/sda5       1,254,203,392 1,453,023,231   198,819,840  83 Linux
/dev/sda6       1,453,025,280 1,465,147,391    12,122,112  82 Linux swap / Solaris
/dev/sda7         956,231,680 1,254,203,391   297,971,712  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        d3ccda81-3863-4f71-9463-33f44f52e69b   ext4       
/dev/sda2        cec3a9c3-c764-435b-b865-d53a725a0f8f   swap       
/dev/sda3        369AA1DC9AA198BF                       ntfs       Windows 7
/dev/sda5        62576e3a-ce3c-4966-a8ea-b1fbbbaae0a0   ext4       
/dev/sda6        045e3fa8-f0be-4251-b1bc-229f924ca9be   swap       
/dev/sda7        d3c1a21c-19d6-4997-95f5-01820faa8d4e   ext4       
/dev/sdb         E2E5-AD00                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/ubuntu/Windows 7  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


```

---

### Post by monkeybrain20122 on 2013-11-21
Apparently when you moved and changed your partitions you have deleted the bootloader. To fix it boot from a live usb , then open a terminal to run

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Now reboot. If it works boot into Ubuntu (in sda1, why do you have two Ubuntu 13.10, another in sda5?) 
Then run
```
sudo update-grub
```

---

### Post by newberry-anthony on 2013-11-21
I tried to reinstall ubuntu from a live usb to fix it. That didn't work so now i have multiple ubuntu directories.

I will try this and report back!

---

### Post by newberry-anthony on 2013-11-21
IT WORKED!!!

Awesome, thanks!

Now my only other question...how can i safely move the partitions and delete older ubuntu installations? I just want this ubuntu installation that is my main one, and my windows 7 installation.

---

### Post by monkeybrain20122 on 2013-11-21
Hi, 

To delete the unneeded Ubuntu partition (sda5 I suppose), boot into the live usb, start gparted and delete /reformat the partition sda5. When done boot into Ubuntu (sda1) and run
sudo update-grub.

---

### Post by oldfred on 2013-11-21
Grub does not use boot flag, but if you ever wanted to boot, repair or reinstall Windows to sda3 you need boot flag on the NTFS partition sda3.
It also looks like PBR or partition boot sector for your NTFS partition is not quite right. You may need to run chkdsk on it to fix it from your Windows repairCD or flash drive.

---

