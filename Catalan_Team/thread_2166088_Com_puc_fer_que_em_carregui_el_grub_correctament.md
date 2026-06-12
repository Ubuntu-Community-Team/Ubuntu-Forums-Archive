---
title: "Com puc fer que em carregui el grub correctament?"
date: 2013-08-07
forum: Catalan Team
---

### Post by pserra on 2013-08-07
Hola,
després de molt de temps disfrutant de l'ubuntu.... torno a tenir problemes...
M'he passat a linux mind per el meu acer aspire one... em va MOLT BÉ
el problema és que vaig modificar particions i vaig aixafar el windows i el vaig instal·lar a una altre partició (el windows) ara ho tinc:


[PHP]pere@pere-aspireoneAO751h ~ $ sudo blkid
[sudo] password for pere: 
/dev/sda1: LABEL="DADES" UUID="1F5326D217CA6FA8" TYPE="ntfs" 
/dev/sda2: LABEL="Windows" UUID="148E860D8E85E816" TYPE="ntfs" 
/dev/sda3: LABEL="SMALL" UUID="569A6255589CAE13" TYPE="ntfs" 
/dev/sda5: LABEL="DADES2" UUID="5DBFBC42572333DA" TYPE="ntfs" 
/dev/sda6: LABEL="COMPARTIT" UUID="6CD0C1D552F304B6" TYPE="ntfs" 
/dev/sda7: UUID="f5413318-5f98-46e7-b6f2-2a255b2a1d81" TYPE="ext4" 
/dev/sda8: UUID="502a905c-2122-48e4-bd8b-1700a6f263a5" TYPE="swap" 
pere@pere-aspireoneAO751h ~ $ [/PHP]

[PHP]pere@pere-aspireoneAO751h ~ $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37c0b349

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    16779263     8388608    7  HPFS/NTFS/exFAT
/dev/sda2        16779264    68968447    26094592    7  HPFS/NTFS/exFAT
/dev/sda3        68968448    81528831     6280192    7  HPFS/NTFS/exFAT
/dev/sda4        81529936   312576704   115523384+   f  W95 Ext'd (LBA)
/dev/sda5        81529938   128406609    23438336    7  HPFS/NTFS/exFAT
/dev/sda6       128409600   281860095    76725248    7  HPFS/NTFS/exFAT
/dev/sda7       281860488   306616319    12377916   83  Linux
/dev/sda8       306616653   312576704     2980026   82  Linux swap / Solaris
pere@pere-aspireoneAO751h ~ $ [/PHP]

si per exemple actualitzo grub amb 
[PHP]pere@pere-aspireoneAO751h ~ $ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found initrd image: /boot/initrd.img-3.5.0-34-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
pere@pere-aspireoneAO751h ~ $ [/PHP]

m'actualitza correctament, tot i que l'arxiu grub.cfg la línia windows no està bé:
(línies on hi ha la referència de windows)
[PHP]### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-1F5326D217CA6FA8' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  1F5326D217CA6FA8
	else
	  search --no-floppy --fs-uuid --set=root 1F5326D217CA6FA8
	fi
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###[/PHP]

Com podeu veure la UUID és la de sda1 enlloc de sda2....
però al engegar ordinador em carrega un altre grub diferent on no em surt el windows i em posa... per exemple a la primera línia:
        Linux Mint 14 nadia..... aquesta línia no és la del grub.cfg...




LA MEVA PREGUNTA ÉS:  COM HO PUC ARREGLAR?
    sembla que l'error pot venir que el sistema té com a partició d'asterisc la sda1 on ara no hi ha rés i potser posant-ho a la sda2 estaria arreglat... com ho arreglo?

Merci

---

### Post by wgarcia on 2013-08-12
Sembla que tens més d'un grub i que està arrencant des d'un lloc que no és el que mires. Com sempre convé córrer el programet boot info script per veure com està la disposició de particions. Em sembla que ja ho havies fet algun cop, les instruccions les pots trobar en aquest missatge:

[http://ubuntuforums.org/showthread.php?t=1811334&p=11083289#post11083289](http://ubuntuforums.org/showthread.php?t=1811334&p=11083289#post11083289)

---

### Post by pserra on 2013-08-15
Hola gràcies wgarcia,
aquests dies no estic a casa... 
ja miraré amb més calma com solventar-lo... deixo el que m'ha generat el programa  Boot Info Script 0.61 
mirant-lo per sobre, no acabo de saber quina es la manera més fàcil de solventar-lo....


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda7 and looks at sector 286341040 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Linux Mint 14 Nadia
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    16,779,263    16,777,216   7 NTFS / exFAT / HPFS
/dev/sda2          16,779,264    68,968,447    52,189,184   7 NTFS / exFAT / HPFS
/dev/sda3          68,968,448    81,528,831    12,560,384   7 NTFS / exFAT / HPFS
/dev/sda4          81,529,936   312,576,704   231,046,769   f W95 Extended (LBA)
/dev/sda5          81,529,938   128,406,609    46,876,672   7 NTFS / exFAT / HPFS
/dev/sda6         128,409,600   281,860,095   153,450,496   7 NTFS / exFAT / HPFS
/dev/sda7         281,860,488   306,616,319    24,755,832  83 Linux
/dev/sda8         306,616,653   312,576,704     5,960,052  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1F5326D217CA6FA8                       ntfs       DADES
/dev/sda2        148E860D8E85E816                       ntfs       Windows
/dev/sda3        569A6255589CAE13                       ntfs       SMALL
/dev/sda5        5DBFBC42572333DA                       ntfs       DADES2
/dev/sda6        6CD0C1D552F304B6                       ntfs       COMPARTIT
/dev/sda7        f5413318-5f98-46e7-b6f2-2a255b2a1d81   ext4       
/dev/sda8        502a905c-2122-48e4-bd8b-1700a6f263a5   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f5413318-5f98-46e7-b6f2-2a255b2a1d81 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f5413318-5f98-46e7-b6f2-2a255b2a1d81

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

title		Linux Mint 14 Nadia, kernel 3.5.0-34-generic
uuid		f5413318-5f98-46e7-b6f2-2a255b2a1d81
kernel		/boot/vmlinuz-3.5.0-34-generic root=UUID=f5413318-5f98-46e7-b6f2-2a255b2a1d81 ro quiet splash
initrd		/boot/initrd.img-3.5.0-34-generic
quiet

title		Linux Mint 14 Nadia, kernel 3.5.0-34-generic (recovery mode)
uuid		f5413318-5f98-46e7-b6f2-2a255b2a1d81
kernel		/boot/vmlinuz-3.5.0-34-generic root=UUID=f5413318-5f98-46e7-b6f2-2a255b2a1d81 ro single
initrd		/boot/initrd.img-3.5.0-34-generic

title		Linux Mint 14 Nadia, memtest86+
uuid		f5413318-5f98-46e7-b6f2-2a255b2a1d81
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7 --hint='hd0,msdos7'  f5413318-5f98-46e7-b6f2-2a255b2a1d81
else
  search --no-floppy --fs-uuid --set=root f5413318-5f98-46e7-b6f2-2a255b2a1d81
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=ca_ES
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Linux Mint 14 Xfce 32-bit, 3.5.0-34-generic (/dev/sda7)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7 --hint='hd0,msdos7'  f5413318-5f98-46e7-b6f2-2a255b2a1d81
	else
	  search --no-floppy --fs-uuid --set=root f5413318-5f98-46e7-b6f2-2a255b2a1d81
	fi
	linux	/boot/vmlinuz-3.5.0-34-generic root=UUID=f5413318-5f98-46e7-b6f2-2a255b2a1d81 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-34-generic
}
menuentry 'Linux Mint 14 Xfce 32-bit, 3.5.0-34-generic (/dev/sda7) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7 --hint='hd0,msdos7'  f5413318-5f98-46e7-b6f2-2a255b2a1d81
	else
	  search --no-floppy --fs-uuid --set=root f5413318-5f98-46e7-b6f2-2a255b2a1d81
	fi
	echo	'Loading Linux 3.5.0-34-generic ...'
	linux	/boot/vmlinuz-3.5.0-34-generic root=UUID=f5413318-5f98-46e7-b6f2-2a255b2a1d81 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.5.0-34-generic
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
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7 --hint='hd0,msdos7'  f5413318-5f98-46e7-b6f2-2a255b2a1d81
	else
	  search --no-floppy --fs-uuid --set=root f5413318-5f98-46e7-b6f2-2a255b2a1d81
	fi
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7 --hint='hd0,msdos7'  f5413318-5f98-46e7-b6f2-2a255b2a1d81
	else
	  search --no-floppy --fs-uuid --set=root f5413318-5f98-46e7-b6f2-2a255b2a1d81
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-1F5326D217CA6FA8' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  1F5326D217CA6FA8
	else
	  search --no-floppy --fs-uuid --set=root 1F5326D217CA6FA8
	fi
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f5413318-5f98-46e7-b6f2-2a255b2a1d81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=502a905c-2122-48e4-bd8b-1700a6f263a5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 134.855621338 = 144.800120832  boot/grub/grub.cfg                             1
 136.723213196 = 146.805432320  boot/grub/menu.lst                             1
 136.542568207 = 146.611466240  boot/grub/stage2                               1
 138.345352173 = 148.547190784  boot/initrd.img-3.5.0-34-generic               2
 137.836059570 = 148.000342016  boot/vmlinuz-3.5.0-34-generic                  2
 138.345352173 = 148.547190784  initrd.img                                     2
 138.345352173 = 148.547190784  initrd.img.old                                 2
 137.836059570 = 148.000342016  vmlinuz                                        2
 137.836059570 = 148.000342016  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 01  |................|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 00 48 cb 02 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff a9 4b  cb 02 07 80 25 09 00 00  |.......K....%...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by pserra on 2013-09-17
Hola,
gràcies wgarcia...
avui m'hi he posat, i seguint els teus savis consells... he cercat informació....al final  he seguit les instruccions d'aquesta pagina:
[http://www.ubuntuleon.com/2012/11/recupera-el-grub-en-ubuntu-1204-y-1210.html]("http://www.ubuntuleon.com/2012/11/recupera-el-grub-en-ubuntu-1204-y-1210.html")
(posant en el meu cas sda7) i ja ho he solventat.
Moltes gràcies

---

