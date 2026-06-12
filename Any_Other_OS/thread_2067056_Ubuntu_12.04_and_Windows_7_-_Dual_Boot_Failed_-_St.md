---
title: "Ubuntu 12.04 and Windows 7 - Dual Boot Failed - Status: 0xc000000f"
date: 2012-10-06
forum: Any Other OS
---

### Post by m.h.shams on 2012-10-06
Hi All,

I have a Dell Latitude running ubuntu 12.04 and windows7. both OS are 64bit and everything was perfect until yesterday. when I received update manager notification in ubuntu. 

there were some new packages to update (I didn't check exactly what). after update, I tried to restart my notebook but I was no longer able to start windows 7. Ubuntu is still ok and running without any issue. 

here is my error in windows startup: 

```
Windows Boot Manager
Windows failed to start. A recent hardware or software chance miht be the cause. To fix the problem:
1. Insert your windows installation disc and restart your computer.
2. Choose your language settings and click "Next."
3. Click "repair your computer."#

Status: 0xc000000f 

```

I've tried windows 7 Repair disk, but it's says: "Not able to fix startup issue automatically"

here is fdisk info : 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      731135      364544    7  HPFS/NTFS/exFAT
/dev/sda2          731136   397716143   198492504    7  HPFS/NTFS/exFAT
/dev/sda4       397717502   500117503    51200001    5  Extended
/dev/sda5       475842560   500117503    12137472   82  Linux swap / Solaris
/dev/sda6       397717504   475842559    39062528   83  Linux

```
Any hope that i can get back my windows ?

---

### Post by nothingspecial on 2012-10-06
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by coffeecat on 2012-10-06
Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity.

That will give use some information about the partition boot sector of the two Windows partitions which may be helpful.

---

### Post by m.h.shams on 2012-10-06
I checked the update history in ubuntu and found that GRUB2 was one of the updated packages and according to [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/716865") most probably that's the cause of issue.

here is output of bootinfoscript:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       731,135       729,088   7 NTFS / exFAT / HPFS
/dev/sda2             731,136   397,716,143   396,985,008   7 NTFS / exFAT / HPFS
/dev/sda4         397,717,502   500,117,503   102,400,002   5 Extended
/dev/sda5         475,842,560   500,117,503    24,274,944  82 Linux swap / Solaris
/dev/sda6         397,717,504   475,842,559    78,125,056  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E2E60DC0E60D95C7                       ntfs       System Reserved
/dev/sda5        4ecb66ad-e4b7-43a3-b089-67d63f1dea04   swap       
/dev/sda6        2779c97e-fb35-4168-a2bd-2dca5be26972   ext4       
/dev/sr0                                                udf        Repair disc Windows 7 64-bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	linux	/boot/vmlinuz-3.2.0-31-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	echo	'Loading Linux 3.2.0-31-generic ...'
	linux	/boot/vmlinuz-3.2.0-31-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-31-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	echo	'Loading Linux 3.2.0-30-generic ...'
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2779c97e-fb35-4168-a2bd-2dca5be26972
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root E2E60DC0E60D95C7
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

=============================== sda6/etc/fstab: ================================

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
UUID=2779c97e-fb35-4168-a2bd-2dca5be26972 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4ecb66ad-e4b7-43a3-b089-67d63f1dea04 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 192.104019165 = 206.270119936  boot/grub/core.img                             1
 199.779327393 = 214.511419392  boot/grub/grub.cfg                             1
 192.339366913 = 206.522822656  boot/initrd.img-3.2.0-23-generic               1
 224.901897430 = 241.486573568  boot/initrd.img-3.2.0-29-generic               2
 197.222209930 = 211.765735424  boot/initrd.img-3.2.0-30-generic               2
 198.853408813 = 213.517221888  boot/initrd.img-3.2.0-31-generic               2
 193.780014038 = 208.069705728  boot/vmlinuz-3.2.0-23-generic                  1
 192.733139038 = 206.945632256  boot/vmlinuz-3.2.0-29-generic                  1
 224.526107788 = 241.083072512  boot/vmlinuz-3.2.0-30-generic                  1
 196.326889038 = 210.804391936  boot/vmlinuz-3.2.0-31-generic                  1
 198.853408813 = 213.517221888  initrd.img                                     2
 197.222209930 = 211.765735424  initrd.img.old                                 2
 196.326889038 = 210.804391936  vmlinuz                                        1
 224.526107788 = 241.083072512  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  49 c8 7c b8 e2 86 68 6c  98 6e 27 e8 db 09 2e 95  |I.|...hl.n'.....|
00000010  0c 1c 6c 26 94 42 91 52  94 ce 3b 61 c9 18 9a 40  |..l&.B.R..;a...@|
00000020  35 fa 9d 67 1b 20 2d 54  97 c4 17 04 bb f7 17 61  |5..g. -T.......a|
00000030  89 90 77 99 36 ca 38 76  cb 3b 1a 62 e0 b7 be 37  |..w.6.8v.;.b...7|
00000040  5e 55 9b f0 11 e5 c3 93  cb c1 78 d9 bd 03 21 d3  |^U........x...!.|
00000050  06 17 79 6a 8a 7f e2 52  c0 23 dc fd bf ad cc 76  |..yj...R.#.....v|
00000060  e5 43 b0 76 90 27 41 31  09 ac c1 be f6 32 84 40  |.C.v.'A1.....2.@|
00000070  aa c6 4b d4 e0 5d d7 b3  f2 cd 01 ee 6a b1 ae 2b  |..K..]......j..+|
00000080  99 42 65 39 d8 fb 11 ba  62 be fd 8e 55 fc fc 72  |.Be9....b...U..r|
00000090  d7 2c e7 e6 37 a3 1c 7f  84 90 11 64 91 89 f1 0a  |.,..7......d....|
000000a0  d6 34 d3 e1 10 6b 9c 9a  e1 8f f1 ee de ba 02 f2  |.4...k..........|
000000b0  d1 e7 9a fb f2 60 6d 97  bf d4 fc b8 b7 65 a6 2b  |.....`m......e.+|
000000c0  ef 78 fb 5a ef 40 59 0c  4c 3a ed 44 79 cc e7 3d  |.x.Z.@Y.L:.Dy..=|
000000d0  9b 5b b0 52 94 9d aa 8b  8b 15 85 b4 77 7c 1e a9  |.[.R........w|..|
000000e0  7b fd 36 a3 1c d3 7b dd  c1 f1 f4 d4 d6 9f 67 42  |{.6...{.......gB|
000000f0  aa 45 ae 54 00 ba aa cf  80 c8 c4 83 77 29 c5 25  |.E.T........w).%|
00000100  98 b0 97 60 db 1e 36 7f  98 60 2e b5 34 a9 c6 f1  |...`..6..`..4...|
00000110  fd e2 0f 38 54 8e d5 b6  a2 a1 83 0a 58 cd a1 ab  |...8T.......X...|
00000120  3d fc 76 d3 71 9b c0 77  fa 1c d9 a4 3c 1c 04 14  |=.v.q..w....<...|
00000130  8e 18 a1 dc af 1f 19 5c  2f cb e0 12 89 84 5d 9d  |.......\/.....].|
00000140  5d d6 c2 91 1d 72 a1 99  6a 51 50 e7 4b 7a 9a dd  |]....r..jQP.Kz..|
00000150  fd 62 ee 49 4d 31 b0 64  90 e1 ac fa 34 a3 c4 f7  |.b.IM1.d....4...|
00000160  06 72 58 89 65 d9 49 a3  fa 04 da 5c c4 9f 8c ae  |.rX.e.I....\....|
00000170  97 10 01 21 44 2c d5 bd  85 6a 64 70 36 cb 55 d4  |...!D,...jdp6.U.|
00000180  e8 61 50 d0 1e 40 52 bb  c8 35 92 2b 57 91 20 be  |.aP..@R..5.+W. .|
00000190  0e 3c 45 8a cf 9c f0 87  c5 9e 6f 68 44 19 cb 23  |.<E.......ohD..#|
000001a0  8b 27 f2 92 bd 43 11 15  99 46 7d 0d 57 0c 9f b1  |.'...C...F}.W...|
000001b0  e5 79 32 a3 ae 1d f5 8d  ae f6 36 0b 77 ef 04 83  |.y2.......6.w...|
000001c0  ff 2f d6 54 73 49 57 f4  3c d4 7c 88 21 f3 cc d4  |./.TsIW.<.|.!...|
000001d0  a7 5b a1 6a df e2 7d 97  a0 d6 08 73 54 c9 aa 47  |.[.j..}....sT..G|
000001e0  4d ae 9b e1 99 92 97 b3  bd b7 8d 4f d0 81 ab 3c  |M..........O...<|
000001f0  14 ed 73 78 99 a7 6c 51  fb 5c 3e b4 fb c0 20 e0  |..sx..lQ.\>... .|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```

---

### Post by coffeecat on 2012-10-06
> **m.h.shams said:**
> I checked the update history in ubuntu and found that GRUB2 was one of the updated packages and according to [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/716865") most probably that's the cause of issue.

To be honest, I'm not 100% convinced that bug is relevant, although you might be right. It's an old bug referring to an earlier version of Ubuntu (and earlier minor version of grub2) - as is the duplicate - and refers to grub corrupting sectors near the start of the drive when attempting to avoid rogue Windows software installed in the embedding area. In your case, if this is what had happened, your sda1 system reserved partition would have been damaged, but it's sda2 (your C: partition) that is the problem with:

```
sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

```

You could try running a chkdsk from the Windows 7 repair disk on sda2, otherwise I don't know what else to suggest.

---

### Post by oldfred on 2012-10-06
I agree with coffeecat. I do not think bug is related and something is corrupting the PBR - partition boot sector of sda2. And sometimes grub gets installed to a NTFS partition which corrupts it, but yours looks like it was corrupted differently as bootscript does not recognize it as grub either.

NTFS does keep a backup of the PBR or Boot sector. You can use testdisk to restore from the backup if the backup is valid.

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Procedure with grub2 installed to PBR, but same for any restore of PBR.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by m.h.shams on 2012-10-07
Thanks for the suggestions, but they didn't work for me. the Problem is that even the Backup boot sector is NOT ok so I can't proceed. 

here is the final screen (step) in the testdisk:

```

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63
     Partition                  Start        End    Size in sectors
 2 P HPFS - NTFS             45 130 22 24756 174 42  396985008

Boot sector
Status: Bad

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.




>[  Quit  ]  [Rebuild BS]  [  Dump  ]
                            Return to Advanced menu

```

---

### Post by oldfred on 2012-10-07
Windows often will not repair a defective BS. 

Use testdisk to RebuildBS. But that creates a XP type NTFS boot sector and you will need to run chkdsk from a Windows 7 repair CD to convert to a Windows 7 type BS.

---

### Post by m.h.shams on 2012-10-07
Rebuild BS was NOT successful. 

I tried windows repair (chkdsk and ...) but it failed too.

It seems that I have to re-install everything. :( sad.

---

