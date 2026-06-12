---
title: "grub comes up empty (no kernels)"
date: 2011-05-11
forum: Apple Hardware Users
---

### Post by god7i11a on 2011-05-11
re/ part of an earlier thread ([http://ubuntuforums.org/showthread.php?t=1695746&page=42):]("http://ubuntuforums.org/showthread.php?t=1695746&page=42%29:") 

in attempting to fix grub2 on my 2011 MBP with 11.04, from the 10.04.2 Ubuntu install CD (10.10 and 11.04 install CDs do not work on the newst MBPs) i chroot and do an update-grub followed bu a grub-install, each of works without error, but on reboot grub comes up with a grub prompt ("grub> ")  but shows NO kernels.

i attach the results of Boot Info Script 0.55 below. as you can see at the bottom, core.img IS located at the sector noted at the top of the results, although when i checked byte-for-byte against the core.img in the /boot/grub folder there is a difference in 2 bytes.

in any case, trying to figure out what comes next to restore grub ... i do not want to have to go back to 10.04.2 and work all the way back to 11.04.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 293593240 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 293857280.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   293,593,239   293,183,600  af HFS
/dev/sda3         293,857,280   489,168,895   195,311,616   c W95 FAT32 (LBA)
/dev/sda4         489,168,896   782,137,647   292,968,752  83 Linux


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   293,593,239   293,183,600 HFS+
/dev/sda3     293,857,280   489,168,895   195,311,616 Linux or Data
/dev/sda4     489,168,896   782,137,647   292,968,752 Linux or Data
/dev/sda5     782,137,648   958,751,359   176,613,712 Linux or Data
/dev/sda6     958,751,360   976,773,134    18,021,775 Linux Swap
/dev/sda7     293,593,240   293,857,279       264,040 Bios Boot Partition

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        4be8f571-321a-3ea2-8d16-8dd53b90452f   hfsplus    Macintosh HD                  
/dev/sda3        8388-14F3                              vfat       BOOTCAMP                      
/dev/sda4        936a71ca-0074-49d7-ab4b-8fd4d15638c7   ext4       Linux                         
/dev/sda5        12c5972c-6e7b-4c0d-a18e-66dfc19241d4   ext4       Home                          
/dev/sda6        86497f4c-2c9a-414e-ac97-3847820708d9   swap                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media                   ext4       (rw)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

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
menuentry 'Ubuntu, with Linux 2.6.38.5' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    linux    /boot/vmlinuz-2.6.38.5 root=UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38.5
}
menuentry 'Ubuntu, with Linux 2.6.38.5 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    echo    'Loading Linux 2.6.38.5 ...'
    linux    /boot/vmlinuz-2.6.38.5 root=UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38.5
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38.5.old' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    linux    /boot/vmlinuz-2.6.38.5.old root=UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38.5.old
}
menuentry 'Ubuntu, with Linux 2.6.38.5.old (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    echo    'Loading Linux 2.6.38.5.old ...'
    linux    /boot/vmlinuz-2.6.38.5.old root=UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38.5.old
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 936a71ca-0074-49d7-ab4b-8fd4d15638c7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root f5bf443497631cd9
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid f5bf443497631cd9 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root f5bf443497631cd9
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid f5bf443497631cd9 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=936a71ca-0074-49d7-ab4b-8fd4d15638c7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=12c5972c-6e7b-4c0d-a18e-66dfc19241d4 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=86497f4c-2c9a-414e-ac97-3847820708d9 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 297.8GB: boot/grub/core.img
 297.8GB: boot/grub/grub.cfg
 252.6GB: boot/initrd.img-2.6.38.5
 250.8GB: boot/initrd.img-2.6.38.5.old
 250.9GB: boot/initrd.img-2.6.38-8-generic
 297.9GB: boot/vmlinuz-2.6.38.5
 297.8GB: boot/vmlinuz-2.6.38.5.old
 253.7GB: boot/vmlinuz-2.6.38-8-generic
 250.9GB: initrd.img
 253.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda7

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 99 e0 7f 11  00 00 00 00 2f 00 20 08  |............/. .|
00000200

```

---

### Post by god7i11a on 2011-05-11
problem solved: Ubuntu, as far as i can tell, never created a device.map ... i ran a grub-mkdevicemap and the grub-install and all is well.

---

