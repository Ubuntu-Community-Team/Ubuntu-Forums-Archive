---
title: "Windows does not boot"
date: 2011-07-03
forum: Any Other OS
---

### Post by gherk432 on 2011-07-03
[INDENT]                             I beseech you, esteemed fellow denizens of the linux forums, to help me with the following minor tangle. 
 
I enter this from the enchanting Ubuntu 11.04, which I installed some  time ago. It loads up happily from the top of my grub 1.99 menu. 
 
The grub menu had the following entries: 
 
Linux ... 
Linux-Recovery ... 
memtest86 ... 
Windows XP ... 
Windows XP Recovery ... 
Windows XP Recovery ... 
 
All of these menu options loaded their kernels correctly from the grub menu. 
 
Well, all but one. My former operating system, Windows XP, would not load with its familiar majestic turpitude. 
 
No. In fact, when I finally needed XP, I selected its menu option in grub 2, and the menu disappeared. 
 
In its place, a single, blinking caret appeared. Just blinking, and  blinking. Taunting me. Threatening me with the prospect that it might  take away my pirated starcraft games forever. Windows had run perfectly  before. 
 
Can anyone help me to understand and defeat this thorny problem? 
 
Though I feel I should not need to say this, I did not engage recovery  of XP from either of the partitions I have available for its restoration  to factory defaults. Yes, I have run "update-grub". 
 
Technical Details: 
EEEPC 1005HA-EU1X-BK
11.04 (Narwhal) 
Kernel Linux 2.6.38-8-generic
Processor 0: N270                         [/INDENT]

---

### Post by gherk432 on 2011-07-04
I intend to use both ubuntu and windows on this machine. I will post the output of fdisk -l, shall we  say, ah, post-haste. Since installing my glorious ubuntu, I have not  booted into XP. My productivity has soared, but without my games I am  starting to become quite the dull boy.

---

### Post by gherk432 on 2011-07-04
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0bf6260

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4301    34545898+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4301       18813   116567041    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3           18814       19451     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda4           19452       19457       48195   ef  EFI (FAT-12/16/32)
/dev/sda5            8829       12777    31707136   83  Linux
/dev/sda6            4301        8829    36369408   17  Hidden HPFS/NTFS
/dev/sda7           18175       18813     5125120    b  W95 FAT32
/dev/sda8           12777       17948    41541632   83  Linux
/dev/sda9           17949       18175     1820672   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders
Units = cylinders of 2352 * 512 = 1204224 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4        3293     3868160    b  W95 FAT32

Disk /dev/dm-0: 1864 MB, 1864368128 bytes
255 heads, 63 sectors/track, 226 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee0c94b1

Disk /dev/dm-0 doesn't contain a valid partition table

```

Please, I would be greatly obliged if anyone could add further insight, or even ask a few questions about this. I would like to get back to my dual-boot bliss.

---

### Post by prodigy_ on 2011-07-04
Actually fdisk alone isn't very helpful when you troubleshoot boot issues. Try to use Boot Info script from my sig and post RESULTS.TXT here.

---

### Post by gherk432 on 2011-07-05
I had a gander at your script's code, and it has impressed me, what little I ken. *Borat voice* Ver' nize. *

On a graver note, I am relieved to see such attention devoted to so common a problem among users of later linux distributions. Damn. 

Anyway, the output follows, below. Please also find it attached, for your viewing pleasure. It seems that for some reason grub is not quite getting to ntldr, but I leave that to your capable eyes to decide for sure. 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    69,091,859    69,091,797   7 NTFS / exFAT / HPFS
/dev/sda2          69,095,422   302,229,503   233,134,082   5 Extended
/dev/sda5         141,834,240   205,248,511    63,414,272  83 Linux
/dev/sda6          69,095,424   141,834,239    72,738,816  17 Hidden NTFS / HPFS
/dev/sda7         291,979,264   302,229,503    10,250,240   b W95 FAT32
/dev/sda8         205,250,560   288,333,823    83,083,264  83 Linux
/dev/sda9         288,335,872   291,977,215     3,641,344  82 Linux swap / Solaris
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192     7,744,511     7,736,320   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 ebf3ddbf-2a3d-4eb0-ab58-7c0ec2e9c680   swap       
/dev/sda1        6C648DAC648D7A1A                       ntfs       
/dev/sda3        CCED-990E                              vfat       PE
/dev/sda5        c4c5e8d6-d3a7-4bac-a799-56cf7033f044   ext4       linroot
/dev/sda6        741426DB0174BC67                       ntfs       windocs
/dev/sda7        CCED-990E                              vfat       PE
/dev/sda8        e4d8c4b5-1d21-439e-a0ed-c73148dc78fc   ext4       linhome
/dev/sdb1        6533-6138                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda6        /windocs                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /home                    ext4       (rw,commit=600)
/dev/sdb1        /media/6533-6138         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition"  
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition"  
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition"  
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition"  
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 11, 2.6.38-8-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4c5e8d6-d3a7-4bac-a799-56cf7033f044 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Linux Mint 11, 2.6.38-8-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4c5e8d6-d3a7-4bac-a799-56cf7033f044 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c4c5e8d6-d3a7-4bac-a799-56cf7033f044
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6C648DAC648D7A1A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root cced-990e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda7)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cced-990e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c4c5e8d6-d3a7-4bac-a799-56cf7033f044 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=e4d8c4b5-1d21-439e-a0ed-c73148dc78fc /home           ext4    defaults        0       2
# /scard1 was on /dev/sdc1 during installation
UUID=3161-6138  /scard1         vfat    utf8,umask=007,gid=46 0       1
# /windocs was on /dev/sda6 during installation
UUID=741426DB0174BC67 /windocs        ntfs    defaults,umask=007,gid=46 0       0
# /windows was on /dev/sda1 during installation
UUID=6C648DAC648D7A1A /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda9 during installation
#UUID=ae946fb9-55ec-4134-8b58-759820a91a60 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.763156891 = 81.350070272   boot/grub/core.img                             1
  95.980491638 = 103.058268160  boot/grub/grub.cfg                             1
  72.008422852 = 77.318455296   boot/initrd.img-2.6.38-8-generic               2
  75.835140228 = 81.427361792   boot/vmlinuz-2.6.38-8-generic                  1
  72.008422852 = 77.318455296   initrd.img                                     2
  75.835140228 = 81.427361792   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```




Please excuse my aside, but I can not yet send private messages. I can not help but agree with the other link you have so graciously included in your signature. I found eight of the points you made to be salient, especially your point about the intel audio drivers, whose subject has caused much distress.

---

### Post by prodigy_ on 2011-07-05
> **gherk432 said:**
> I had a gander at your script's code, and it has impressed me, what little I ken. *Borat voice* Ver' nize. *
(Just to clarify) I'm not the author. Though this script is indeed impressive. :)

Anyway, I found nothing suspicious re. your boot configuration. Everything seems to be in place. Particularly this entry in grub.cfg```
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6C648DAC648D7A1A
    drivemap -s (hd0) ${root}
    chainloader +1
}
```
points in the right direction so to speak.

One thing of notice is that your Windows system partition (/dev/sda1) is set to be mounted in read-write mode via fstab. While this is technically correct, it's not advisable because it leaves system files unprotected. Are you sure your Windows installation is intact?

---

### Post by Perfect Storm on 2011-07-05
Moved to Other OS/Distro Talk.

---

### Post by gherk432 on 2011-07-11
I am not sure whether the windows installation is intact. I would prefer that it was. How might I tell? 

Perhaps I will have to re-install windows, and attempt to repair the GRUB configuration.

---

