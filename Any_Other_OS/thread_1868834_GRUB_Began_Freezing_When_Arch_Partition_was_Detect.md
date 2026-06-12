---
title: "GRUB Began Freezing When Arch Partition was Detected"
date: 2011-10-24
forum: Any Other OS
---

### Post by AbsolutelyRidiculous on 2011-10-24
I recently upgraded to 11.10, however, when GRUB does its little "no wubildr" error phase (when it usually skips it and continues to operate normally) it now freezes upon discovering hd0,3. It literally says:

Try (hd0,0): NTFS5: No wubildr
and continues going down the partitions until..
Try (hd0,3): EXT2:

And freezes. Nothing going on. I'm forced to either shut down or use ctrl-alt-delete to bring back my BIOS.

This is the partition that Arch Linux resides on. Before the upgrade, GRUB did not know about the partition because Arch was installed after Ubuntu; therefore there was no issue. Is there a way that I can fix this? Is this a wubi-related issue? Am I royally screwed and forced to reinstall? I will NEVER use wubi again if it is the problem, since I have encountered GRUB-related issues before.

---

### Post by AbsolutelyRidiculous on 2011-10-26
Bump? It's been well over a day and there have been no replies.

---

### Post by oldfred on 2011-10-26
Moved to other OS.

Post this, but wubi is just a file inside your NTFS partition and boots thru Windows.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by AbsolutelyRidiculous on 2011-10-27
Thank you for your reply! I am not booting FROM Arch, but from the GRUB supplied from Ubuntu itself. However, if it still helps, I have put my RESULTS.txt here:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048    24,782,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          24,782,848   456,796,159   432,013,312   7 NTFS / exFAT / HPFS
/dev/sda4         456,796,160   488,396,799    31,600,640  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        E624135D24133053                       ntfs       SYSTEM RESERVED
/dev/sda3        24A43690A4366488                       ntfs       Gateway
/dev/sda4        8d33d8e5-10d5-4ebe-8406-7b85cdf107ef   ext4       archlin

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,relatime,user_xattr,acl,barrier=1,data=ordered)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 24A43690A4366488
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 24A43690A4366488
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 24A43690A4366488
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=24A43690A4366488 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 24A43690A4366488
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=24A43690A4366488 loop=/ubuntu/disks/root.disk ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 24A43690A4366488
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=24A43690A4366488 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 24A43690A4366488
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=24A43690A4366488 loop=/ubuntu/disks/root.disk ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 8d33d8e5-10d5-4ebe-8406-7b85cdf107ef
	linux /boot/vmlinuz-linux root=/dev/sda4 ro
	initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux Fallback (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 8d33d8e5-10d5-4ebe-8406-7b85cdf107ef
	linux /boot/vmlinuz-linux root=/dev/sda4 ro
	initrd /boot/initramfs-linux-fallback.img
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

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  10.977428436 = 11.786924032   boot/grub/grub.cfg                             1
  17.890625000 = 19.209912320   boot/initrd.img-2.6.38-11-generic              2
  16.054187775 = 17.238052864   boot/initrd.img-3.0.0-12-generic              64
   6.586250305 = 7.071932416    boot/vmlinuz-2.6.38-11-generic                 1
   5.969184875 = 6.409363456    boot/vmlinuz-3.0.0-12-generic                  2
  17.890625000 = 19.209912320   initrd.img.old                                 2
   5.969184875 = 6.409363456    vmlinuz                                        2
   6.586250305 = 7.071932416    vmlinuz.old                                    1

=========================== sda4/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1

# (0) Arch Linux
title  Arch Linux
root   (hd0,3)
kernel /boot/vmlinuz-linux root=/dev/sda4 ro
initrd /boot/initramfs-linux.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,3)
kernel /boot/vmlinuz-linux root=/dev/sda4 ro
initrd /boot/initramfs-linux-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>	<dir>	<type>	<options>	<dump>	<pass>
tmpfs		/tmp	tmpfs	nodev,nosuid	0	0
LABEL=archlin / ext4 defaults 0 1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 221.946701050 = 238.313455616  boot/grub/menu.lst                             1
 229.966064453 = 246.924181504  boot/grub/stage2                               1
 218.139068604 = 234.225041408  boot/initramfs-linux-fallback.img              1
 218.124130249 = 234.209001472  boot/initramfs-linux.img                       1
 229.944561005 = 246.901092352  boot/vmlinuz-linux                             1

=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

```

Also, I have two questions: is it just simpler to boot Ubuntu from the legacy GRUB that I got from Arch, and can I just copypaste the entries for the newer (Ubuntu) GRUB into the config file for the old (Arch-Supplied) GRUB? Thank you for your help!

---

### Post by oldfred on 2011-10-27
You have wubi not a partitioned install of Ubuntu. You cannot (easily) boot wubi from grub. Wubi uses the windows boot loader to boot and is just a file inside the Windows NTFS partition. If using Ubuntu a lot, then a partitioned install is recommended, but you have used all 4 primary partitions, so you have to reconfigure to create the extended partition. Ubuntu will boot from logical partitions in the extended without issue.

Does Arch boot ok?

Is it the script showing duplicates or do you have duplicate entires in Windows? Usually that prevents Windows from booting as it is not case sensitive and sees two identical entries. Both sda1 & sda2.

>     Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

You should have only one /bootmgr and one /Boot/BCD regardless of case. If you have multiples, copy all but one to another location just in case that is the working copy and delete from the root of Windows.

---

### Post by AbsolutelyRidiculous on 2011-10-30
Both Arch and Windows boot absolutely fine. WUBI installed GRUB 'underneath' the Windows bootloader, which means that when I select Ubuntu from the Windows bootloader, I get the Ubuntu GRUB, which freezes when coming across the messages that I mentioned in the OP. Therefore, I cannot boot *Ubuntu*.

My setup was a script-kiddie kind of setup. Because Arch, Windows, and Ubuntu all had their own bootloaders, my computer goes through these phases:

1. My computer starts up and my BIOS loads up, starting my bootloader.
2. Legacy GRUB that came from Arch Linux loads, presenting me with an option to choose Windows or Arch Linux. If I choose Arch Linux, it starts up.
3. If I choose Windows, the Windows bootloader starts up and I'm greeted with a choice of Windows or Ubuntu. If I choose Windows, it boots up without incident.
4. If I choose Ubuntu, the newer GRUB starts up, gives me the "no wubildr" messages and then freezes upon trying "(hd0,3)" which is my Arch Linux partition.

Before the upgrade, the new GRUB was unaware of my arch partition; it found that there was "no wubildr" in the partitions it was aware of, did not freeze, and continued to list Ubuntu, older versions of Ubuntu, "Windows Recovery Environment" (which is my manufacturer's factory reset wizard) and "Windows (loader)" which releases me back into the Windows bootloader.

Also, is there a way that I can get an Ubuntu live distro that fits in a 256mb USB drive that does most of the install via download? Is this usable? Also, can you link me somewhere where I can learn to make logical paritions for Ubuntu? I learned how to do regular ones via internet tutorial, but I'm not sure if logical has a similar procedure.

---

### Post by oldfred on 2011-10-30
There is an Ubuntu minimal. It really is just a kernel & a few drivers, not sure how small it is.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

There are 4 primary partitions, one can be the extended which can hold many logical partitions. Once you have the extended you are creating logicals inside the extended.
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

