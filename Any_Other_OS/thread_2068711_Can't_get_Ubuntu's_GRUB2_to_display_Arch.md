---
title: "Can't get Ubuntu's GRUB2 to display Arch"
date: 2012-10-09
forum: Any Other OS
---

### Post by Bastiat on 2012-10-09
Hi,
I have been trying for the past few days to get a dual boot of Ubuntu 11.10 and Archlinux going. I can get both os's functioning, but I am unable to get GRUB2 to show Arch. Likewise, if I install arch's grub, I can't get Ubuntu to show up.

I'm partitioned as follows:
sda2 =/home
sda3 =/swap
sda4 =/boot
sda5 =/arch
sda6 =/ubuntu 11.10
sda7 = freespace

I ran a bootinfoscript as described in a reply to a similar (but different enough) question:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Arch Linux ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /extlinux/extlinux.conf /grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:  Syslinux looks at sector 1493912 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               4,094    92,162,047    92,157,954   5 Extended
/dev/sda5               4,096    30,724,095    30,720,000  83 Linux
/dev/sda6          30,726,144    61,446,143    30,720,000  83 Linux
/dev/sda7          61,448,192    92,162,047    30,713,856  83 Linux
/dev/sda2          92,162,048   478,975,999   386,813,952  83 Linux
/dev/sda3         478,976,000   487,167,999     8,192,000  82 Linux swap / Solaris
/dev/sda4    *    487,168,000   488,396,799     1,228,800  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.2 GB, 16231956480 bytes
256 heads, 54 sectors/track, 2293 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,703,039    31,703,008   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        31ba7460-8918-4fd1-9b33-e0cd280de3f4   ext4       /home
/dev/sda3        6c65ac25-376b-4a7e-ab96-e8ff186046b5   swap       swap
/dev/sda4        f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e   ext4       
/dev/sda5        2cd1bd50-2f3b-4219-b09f-5b3bf460be7a   ext4       Archlinux
/dev/sda6        37c6768c-5ef8-4737-a4a7-32efc39e844f   ext4       
/dev/sda7        902b094a-62e5-4001-b4ec-884ad6341b63   ext4       New Distro
/dev/sdb1        5440-DF84                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /home                    ext4       (rw,commit=0)
/dev/sda4        /boot                    ext4       (rw,commit=0)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/5440-DF84         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
#
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
# UUID=2cd1bd50-2f3b-4219-b09f-5b3bf460be7a LABEL=Archlinux
/dev/sda5               /             ext4          rw,relatime,data=ordered    0 1

# UUID=31ba7460-8918-4fd1-9b33-e0cd280de3f4 LABEL=/home
/dev/sda2               /home         ext4          rw,relatime,data=ordered    0 2

# UUID=2b12c742-6338-4af0-a97c-de7c16bb8112 LABEL=/boot
#/dev/sda4               /boot         ext4          rw,relatime,data=ordered    0 2

#UUID=2b12c742-6338-4af0-a97c-de7c16bb8112    /boot    ext4    defaults    0    2
UUID=2b12c742-6338-4af0-a97c-de7c16bb8112    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=37c6768c-5ef8-4737-a4a7-32efc39e844f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda4 during installation
UUID=f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e /boot           ext4    defaults        0       2
# /home was on /dev/sda2 during installation
UUID=31ba7460-8918-4fd1-9b33-e0cd280de3f4 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=6c65ac25-376b-4a7e-ab96-e8ff186046b5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                initrd.img.old                                 2
               =                vmlinuz.old                                    1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

============================= sda4/grub/grub.cfg: ==============================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 37c6768c-5ef8-4737-a4a7-32efc39e844f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos4)'
  search --no-floppy --fs-uuid --set=root f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e
    linux    /vmlinuz-2.6.38-8-generic root=UUID=37c6768c-5ef8-4737-a4a7-32efc39e844f ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=37c6768c-5ef8-4737-a4a7-32efc39e844f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root f0aa9c04-0ef3-43f8-bc5b-8a1863cc947e
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Arch Linux" {
    insmod ext2
    set root=(hd0,5)
    linux /vmlinuz-linux root=UUID=2cd1bd50-2f3b-4219-b09f-5b3bf460be7a
    initrd /initramfs-linux.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

========================= sda4/extlinux/extlinux.conf: =========================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-2.6.38-8-generic                    2
               =                vmlinuz-2.6.38-8-generic                       1

================= sda4: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

               =                extlinux/chain.c32                             1
               =                extlinux/extlinux.conf                         1

============== sda4: Version of COM32(R) files used by Syslinux: ===============

 extlinux/chain.c32                 :  COM32R module (v4.xx)

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/bobby/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```I loaded the /dev/sda5 to /mnt and used os-prober, followed by update-grub. This got it to appear, but now when I click on Arch Linux in GRUB, it gives:
Error: You need to load a kernel first

I don't know what exactly to do to boot into arch now.

Any help would be appreciated.

---

### Post by oldfred on 2012-10-10
It looks like you are trying to use the same /boot for both installs. You cannot share a /boot partition. Either leave /boot inside the / (root) or have a separate /boot partition for every install. I prefer to not have a separate /boot partition as it just adds a partition.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Bastiat on 2012-10-10
Hey thanks much for the reply and the link! I'll make note of this.

---

