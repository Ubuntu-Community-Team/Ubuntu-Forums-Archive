---
title: "Installation error messages"
date: 2011-09-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ChrisOfBristol on 2011-09-03
It keeps hanging, sometimes it comes back to life after waiting five minutes, once or twice it has rebooted itself.

I suspected overheating, so cleaned out the fan, put new grease on the graphics card heatsink and a fan on it. Everything is running very cool (processor monitor says it is 40C). So it can't be overheating.

The computer is unusable because of this.

What should I try next?

---

### Post by ChrisOfBristol on 2011-09-12
After Ubuntu, I tried Fedora and Mint without any improvement, but in swapping CDs and disk drives around I've discovered that it seems to be ok from a live DVD (PATA) with no hard disk drive (PATA) attached, although there was nothing wrong with either of the disk drives I had used. The cable looks fine and I use the correct jumpers on the drives. I have also run a memory check.

---

### Post by ChrisOfBristol on 2011-09-13
It has now crashed into a terminal screen - showing these messages:

12457.560118 Kernel panic, not syncing, attempted to kill init.
12457.560230 pid:1, comm: init not tainted 2.6.38-8-generic #42-ubuntu 
12457.560318 Call Trace:
-(Lots of lines)
-
-
-
12457.561659 panic occurred, switching back to text console

---

### Post by Rubi1200 on 2011-09-13
I suggest you post the results of the boot info script so we can get a better overview of the current state of your system,

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by ChrisOfBristol on 2011-09-13
> **Rubi1200 said:**
> I suggest you post the results of the boot info script...
I've run this as suggested, NB there was a warning that it could not find awk so used busybox awk.
Nautilus shows two floppy drives even though I have none and there is no reference to them in the BIOS editor.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Syslinux 3.53-3.86
    Boot sector info:   Syslinux looks at sector 528 of /dev/sdb1 for its 
                       second stage. It is very unlikely that Syslinux is 
                       (still) installed. The second stage could not be 
                       found. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    25,189,919    25,189,857  83 Linux
/dev/sda2          25,189,981   156,296,384   131,106,404   5 Extended
/dev/sda5          25,189,983    33,367,004     8,177,022  82 Linux swap / Solaris
/dev/sda6          33,367,068   156,296,384   122,929,317  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1028 MB, 1028653056 bytes
16 heads, 32 sectors/track, 3924 cylinders, total 2009088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     2,009,087     2,009,056   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1d3b0d8c-0aa3-4df8-b424-5058184b6678   ext3       
/dev/sda5        4a3af238-0777-4d0d-af85-e25149101ccc   swap       
/dev/sda6        ac1a0741-6076-441f-9632-3f6a89795f45   ext3       
/dev/sdb1        D234-34B9                              vfat       UDISK 2.0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext3       (rw,commit=0)
/dev/sdb1        /media/UDISK 2.0         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=1d3b0d8c-0aa3-4df8-b424-5058184b6678 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=1d3b0d8c-0aa3-4df8-b424-5058184b6678 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=1d3b0d8c-0aa3-4df8-b424-5058184b6678 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=1d3b0d8c-0aa3-4df8-b424-5058184b6678 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1d3b0d8c-0aa3-4df8-b424-5058184b6678
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ac1a0741-6076-441f-9632-3f6a89795f45 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4a3af238-0777-4d0d-af85-e25149101ccc none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.877086163 = 2.015505920    boot/grub/core.img                             1
   1.877093792 = 2.015514112    boot/grub/grub.cfg                             1
   1.929580212 = 2.071870976    boot/initrd.img-2.6.38-11-generic             10
   2.006232738 = 2.154176000    boot/initrd.img-2.6.38-8-generic               6
   1.902816296 = 2.043133440    boot/vmlinuz-2.6.38-11-generic                 3
   1.929381847 = 2.071657984    boot/vmlinuz-2.6.38-8-generic                  3
   1.929580212 = 2.071870976    initrd.img                                    10
   2.006232738 = 2.154176000    initrd.img.old                                 6
   1.902816296 = 2.043133440    vmlinuz                                        3
   1.929381847 = 2.071657984    vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  00 00 01 ba 44 03 bf 32  3c 01 01 89 c3 f8 00 00  |....D..2<.......|
00000010  01 bd 07 ec 81 80 05 21  00 f1 10 0f 80 02 01 e4  |.......!........|
00000020  41 90 a1 6f 31 62 88 96  d3 f3 7c f5 7c 22 f4 65  |A..o1b....|.|".e|
00000030  6e ec 6b 20 c2 8b 6b a5  31 89 e4 58 96 5b 45 27  |n.k ..k.1..X.[E'|
00000040  0f 05 93 26 a9 24 ac 73  0a f6 c2 cc e5 4f 88 60  |...&.$.s.....O.`|
00000050  03 27 45 f4 e1 9c 03 2c  a6 70 54 cc 1f 46 8c fa  |.'E....,.pT..F..|
00000060  03 8d e4 97 54 5f 75 46  12 17 46 c3 22 1a d4 b1  |....T_uF..F."...|
00000070  da 18 aa 28 c7 2f a4 23  20 db e3 13 84 9d 34 af  |...(./.# .....4.|
00000080  a4 75 46 d8 92 62 16 bd  fa 47 ca ca dc e5 fb 4f  |.uF..b...G.....O|
00000090  83 06 94 97 d3 8d f6 f4  16 bd b5 55 57 f1 d4 8b  |...........UW...|
000000a0  bd 95 8d ca 49 bc 83 e5  34 ad 8f 77 5b 48 a5 c4  |....I...4..w[H..|
000000b0  e4 51 2d 39 be 9b 14 79  2a 47 06 98 00 3f 56 b3  |.Q-9...y*G...?V.|
000000c0  36 90 02 29 e6 29 7a 4a  7b 83 73 41 3e a8 46 33  |6..).)zJ{.sA>.F3|
000000d0  24 83 5f ca 66 cd 79 a5  93 62 4e 82 b3 52 4e b6  |$._.f.y..bN..RN.|
000000e0  e9 4c 26 c5 76 a6 04 61  1b 94 8e fb 92 ba f1 2d  |.L&.v..a.......-|
000000f0  9c 76 0f 6e 8c 22 62 df  05 51 de dd 4c 5d e3 a5  |.v.n."b..Q..L]..|
00000100  ff c8 d2 75 43 75 1c e9  51 c0 39 07 24 8b 53 4a  |...uCu..Q.9.$.SJ|
00000110  5d 6c ba c3 56 1c a3 c0  84 5c 30 81 8b 5a 42 3c  |]l..V....\0..ZB<|
00000120  6d ea 3b 5d af 66 f8 86  00 09 87 8b 88 59 f6 f4  |m.;].f.......Y..|
00000130  34 9f 51 36 fe 04 5e 18  e8 b7 fe 3c 96 17 06 37  |4.Q6..^....<...7|
00000140  89 6a 72 d6 f8 b0 9a 47  11 a4 a9 da 9b 7c 1c b5  |.jr....G.....|..|
00000150  22 0c 6b 5a d7 24 8e 7b  5a f5 7c 1a 37 fc b6 be  |".kZ.$.{Z.|.7...|
00000160  4f 02 62 69 d2 3e eb 0b  06 f6 97 aa 0c 91 7e 16  |O.bi.>........~.|
00000170  c8 da db af a8 40 0c 6a  96 19 a2 23 b6 4e 1e 5a  |.....@.j...#.N.Z|
00000180  82 78 ad 11 df 12 a4 6b  ec 4c 83 56 d4 1f 2a 36  |.x.....k.L.V..*6|
00000190  92 46 be 21 80 01 bd f1  6c eb 70 c3 96 cc c6 cf  |.F.!....l.p.....|
000001a0  36 cb 09 0c 43 1b 84 30  56 c6 43 e4 3d ac 85 9d  |6...C..0V.C.=...|
000001b0  72 51 68 d8 c6 4f 4c 17  6f 1e bf 76 41 73 00 fe  |rQh..OL.o..vAs..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 7e c5 7c 00 00 fe  |..........~.|...|
000001d0  ff ff 05 fe ff ff 80 c5  7c 00 e4 c0 53 07 00 00  |........|...S...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Rubi1200 on 2011-09-13
I don't see anything immediately wrong with the boot script results and clearly you have taken other steps to try and isolate the problem.

Did you recently install some software or updates that may have led to this?

Have you tried booting an older kernel to see if the problem persists?

---

### Post by ChrisOfBristol on 2011-09-14
I only installed Ubuntu on this computer last week and it has had the problem since. I re-installed once just in case. I'll try running on the earlier kernel as you suggest and see what happens.

---

### Post by ChrisOfBristol on 2011-09-15
After finding this suggestion: [HTML]http://ubuntuforums.org/showthread.php?t=1589135[/HTML] I disabled 'Enhanced Intel Speedstep Technology' in the BIOS. The computer has now run a couple of hours with me using it, and all night without. I can't be certain that this has fixed it because the freezes were unpredictable, but they always happened within 5 minutes to two hours of switching on the computer, so I'm very hopeful! 

It's now been working without any problems since 15/9/2011 so I am confident that disabling Speedstep in the BIOS has fixed it.

---

### Post by rafe_b on 2012-01-08
> **ChrisOfBristol said:**
> After finding this suggestion: [HTML]http://ubuntuforums.org/showthread.php?t=1589135[/HTML] I disabled 'Enhanced Intel Speedstep Technology' in the BIOS.

And as of 1/8/12, I can confirm another instance of this same fix working nicely on an Asus Pundit P1-PH1 desktop PC from geeks.com.

The symptoms were random freezes (no response from mouse or keyboard, but video still intact) which occasionally un-froze on their own.  The computer has worked fine for >8 hrs (so far) since making this one change to the BIOS settings.

---

### Post by ChrisOfBristol on 2012-01-08
> **rafe_b said:**
> And as of 1/8/12, I can confirm another instance of this same fix working nicely

Thanks for confirming it, and mine has worked perfectly ever since my post of 15th September last year (four months), so there's no doubt about the cause and cure now.

---

