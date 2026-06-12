---
title: "MBR question (sorry if it is a dumb question :/ )"
date: 2011-09-05
forum: Any Other OS
---

### Post by racie on 2011-09-05
Hey guys, I installed Linux Mint as a dual-boot on my brother's PC so he could give it a whirl.  It turns out he doesn't like it so I was going to uninstall it for him.  Normally, I would take the time to enter some commands into the terminal to restore the master boot record of the HDD.  My setup is like this: HDD1 = Windows, HDD2 = Linux

However, I have a question that is probably pretty obvious, so I apologize for my lack of knowledge.  :P

Anyway, I was going to do a complete reinstall of Windows for him as well for other reasons.

Now, if I format both of the HDD's and reinstall Windows, will the MBR be restored without having to do other steps?

Thanks for looking at my very nooby question.

---

### Post by linuxman94 on 2011-09-05
It depends on which hdd you installed the bootloader on.  If it's installed on the hdd that you are going to install windows on,  windows will overwrite the mbr when you install it.  To be sure, post the result of this script:

[Boot info script]("http://bootinfoscript.sourceforge.net/")

---

### Post by racie on 2011-09-06
Ahh yes... I was pretty sure that the bootloader was installed to the first hard disk, but I ran the boot info script just to make sure.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 KDE
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.3 GB, 15307407360 bytes
255 heads, 63 sectors/track, 1861 cylinders, total 29897280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    28,547,071    28,545,024  83 Linux
/dev/sdb2          28,549,118    29,896,703     1,347,586   5 Extended
/dev/sdb5          28,549,120    29,896,703     1,347,584  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 128 MB, 128450560 bytes
141 heads, 61 sectors/track, 29 cylinders, total 250880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       249,855       247,808   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9AC00924C0090869                       ntfs       
/dev/sdb1        f157e3bb-a447-4ca1-9843-8ea335162216   ext4       
/dev/sdb5        2ddc153e-f71a-4e6d-96d9-46d07f0ef9d5   swap       
/dev/sdc1        542C-93FB                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/542C-93FB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
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
menuentry 'Linux Mint 10 KDE, 2.6.35-22-generic (/dev/sdb1)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f157e3bb-a447-4ca1-9843-8ea335162216 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10 KDE, 2.6.35-22-generic (/dev/sdb1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f157e3bb-a447-4ca1-9843-8ea335162216 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set f157e3bb-a447-4ca1-9843-8ea335162216
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 9ac00924c0090869
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=f157e3bb-a447-4ca1-9843-8ea335162216 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=2ddc153e-f71a-4e6d-96d9-46d07f0ef9d5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.367027283 = 4.689059840    boot/grub/core.img                             1
   4.370330811 = 4.692606976    boot/grub/grub.cfg                             1
   2.914489746 = 3.129409536    boot/initrd.img-2.6.35-22-generic              1
   4.379974365 = 4.702961664    boot/vmlinuz-2.6.35-22-generic                 1
   2.914489746 = 3.129409536    initrd.img                                     1
   4.379974365 = 4.702961664    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  96 d6 00 00 c0 35 18 00  fa 00 00 00 02 00 0b 00  |.....5..........|
00000010  b0 d6 00 00 c0 96 18 00  c2 00 00 00 02 00 0b 00  |................|
00000020  bb d6 00 00 c0 8a 18 00  bb 00 00 00 02 00 0b 00  |................|
00000030  c9 d6 00 00 d0 80 18 00  43 02 00 00 02 00 0b 00  |........C.......|
00000040  e2 d6 00 00 30 ff 18 00  5f 02 00 00 02 00 0b 00  |....0..._.......|
00000050  ff d6 00 00 c0 0d 19 00  6e 01 00 00 02 00 0b 00  |........n.......|
00000060  13 d7 00 00 10 25 19 00  26 01 00 00 02 00 0b 00  |.....%..&.......|
00000070  2f d7 00 00 40 a6 18 00  0d 01 00 00 02 00 0b 00  |/...@...........|
00000080  46 d7 00 00 70 fc 18 00  b8 02 00 00 02 00 0b 00  |F...p...........|
00000090  60 d7 00 00 a0 f9 18 00  c9 02 00 00 02 00 0b 00  |`...............|
000000a0  7e d7 00 00 b0 23 19 00  55 01 00 00 02 00 0b 00  |~....#..U.......|
000000b0  9b d7 00 00 10 f4 18 00  dc 01 00 00 02 00 0b 00  |................|
000000c0  b3 d7 00 00 40 f2 18 00  ca 01 00 00 02 00 0b 00  |....@...........|
000000d0  cf d7 00 00 90 21 19 00  10 01 00 00 02 00 0b 00  |.....!..........|
000000e0  ea d7 00 00 c0 f7 18 00  dc 01 00 00 02 00 0b 00  |................|
000000f0  02 d8 00 00 f0 f5 18 00  ca 01 00 00 02 00 0b 00  |................|
00000100  1e d8 00 00 a0 22 19 00  10 01 00 00 02 00 0b 00  |....."..........|
00000110  39 d8 00 00 70 f0 18 00  c2 01 00 00 02 00 0b 00  |9...p...........|
00000120  4f d8 00 00 50 eb 18 00  ca 01 00 00 02 00 0b 00  |O...P...........|
00000130  69 d8 00 00 80 20 19 00  06 01 00 00 02 00 0b 00  |i.... ..........|
00000140  82 d8 00 00 20 ed 18 00  46 03 00 00 02 00 0b 00  |.... ...F.......|
00000150  9a d8 00 00 20 e8 18 00  27 03 00 00 02 00 0b 00  |.... ...'.......|
00000160  b6 d8 00 00 70 1f 19 00  06 01 00 00 02 00 0b 00  |....p...........|
00000170  d1 d8 00 00 30 e6 18 00  e4 01 00 00 02 00 0b 00  |....0...........|
00000180  e7 d8 00 00 d0 e1 18 00  f4 01 00 00 02 00 0b 00  |................|
00000190  01 d9 00 00 50 1e 19 00  17 01 00 00 02 00 0b 00  |....P...........|
000001a0  1a d9 00 00 70 5e 18 00  b7 06 00 00 02 00 0b 00  |....p^..........|
000001b0  30 d9 00 00 b0 57 18 00  bd 06 00 00 02 00 00 fe  |0....W..........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 14 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 26 00  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 c8 03 00 c1 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 fb 93 2c 54 4e  4f 20 4e 41 4d 45 20 20  |..)..,TNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 66 31 c0 8e d8 8e  |  FAT32   f1....|
00000060  d0 bc 00 7c 88 16 08 7a  fc fb 68 00 08 07 66 0f  |...|...z..h...f.|
00000070  b7 1e 0e 7c 66 89 1e 00  7a a0 10 7c 66 f7 26 24  |...|f...z..|f.&$|
00000080  7c 66 01 d8 66 0f b6 1e  0d 7c 01 db 66 29 d8 66  ||f..f....|..f).f|
00000090  a3 04 7a 66 a1 2c 7c 66  25 ff ff ff 0f 31 db 89  |..zf.,|f%....1..|
000000a0  df 66 50 e8 64 00 0f b6  0e 0d 7c c1 e1 04 26 80  |.fP.d.....|...&.|
000000b0  3d 00 74 4e 51 57 b9 0b  00 be c2 7d f3 a6 5f 59  |=.tNQW.....}.._Y|
000000c0  74 0e 83 c7 20 e2 e7 66  58 e8 90 00 73 34 72 cd  |t... ..fX...s4r.|
000000d0  66 58 26 8b 45 14 25 ff  0f 66 c1 e0 10 26 8b 45  |fX&.E.%..f...&.E|
000000e0  1a 31 db 66 50 e8 22 00  8c c0 0f b6 0e 0d 7c c1  |.1.fP.".......|.|
000000f0  e1 05 01 c8 8e c0 66 58  e8 61 00 72 e4 ea 00 80  |......fX.a.r....|
00000100  00 00 be b1 7d e8 9a 00  eb fe 66 0f b6 0e 0d 7c  |....}.....f....||
00000110  66 f7 e1 66 03 06 04 7a  66 03 06 1c 7c 06 66 60  |f..f...zf...|.f`|
00000120  6a 00 6a 00 66 50 06 53  83 e9 7f 19 c0 21 c8 83  |j.j.fP.S.....!..|
00000130  c0 7f 50 c1 e0 05 8c c1  01 c1 8e c1 6a 10 b8 00  |..P.........j...|
00000140  42 8a 16 08 7a 89 e6 cd  13 be d0 7d 72 b7 61 66  |B...z......}r.af|
00000150  61 66 83 c0 7f 83 e9 7f  77 c4 07 c3 06 1e 07 bb  |af......w.......|
00000160  00 7e 66 50 66 c1 e8 07  66 3b 06 f0 7d 74 0f 66  |.~fPf...f;..}t.f|
00000170  a3 f0 7d 66 03 06 00 7a  b9 01 00 e8 9a ff 66 58  |..}f...z......fX|
00000180  66 83 e0 7f 67 66 8b 04  85 00 7e 00 00 66 25 ff  |f...gf....~..f%.|
00000190  ff ff 0f 66 3d f7 ff ff  0f be e2 7d 0f 84 65 ff  |...f=......}..e.|
000001a0  07 c3 ac 84 c0 74 09 b4  0e bb 07 00 cd 10 eb f2  |.....t..........|
000001b0  c3 43 61 6e 6e 6f 74 20  66 69 6e 64 20 66 69 6c  |.Cannot find fil|
000001c0  65 20 4d 54 4c 44 5f 46  33 32 20 20 20 0d 0a 00  |e MTLD_F32   ...|
000001d0  44 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 0d  |Disk read error.|
000001e0  0a 00 42 61 64 20 63 6c  75 73 74 65 72 0d 0a 00  |..Bad cluster...|
000001f0  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

Yup.  There it is.  So the MBR will be fine once I install Windows?

Sounds good.  Thanks.

---

### Post by e79 on 2011-09-06
> **racie said:**
> Now, if I format both of the HDD's and reinstall Windows, will the MBR be restored without having to do other steps?

Maybe I missed something...but why would you care about a leftover MBR if you are about to wipe your drives and reinstall Windows only (that will reinstall a MBR anyway) ?

If this is what intended, I suggest you to zero-out your drive (using DBAN or KillDisk) and then simply reinstall Windows.

Just my $0.02

---

### Post by drs305 on 2011-09-06
> **racie said:**
> 
Yup.  There it is.  So the MBR will be fine once I install Windows?


Yes it will. You say you need to reinstall Windows for other reasons as well, but for starters if all you need is to get Windows booting again, and you are currently running an ubuntu cd, you can just run the following commands to restore the mbr to point to Windows:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
It will complain about lilo not being completely installed, but forget the messages and only run the above commands. Rebooting should restore the Windows boot.

---

### Post by racie on 2011-09-06
> **e79 said:**
> Maybe I missed something...but why would you care about a leftover MBR if you are about to wipe your drives and reinstall Windows only (**that will reinstall a MBR anyway**) ?

If this is what intended, I suggest you to zero-out your drive (using DBAN or KillDisk) and then simply reinstall Windows.

Just my $0.02
That's why it was a dumb question.  I wasn't sure if the new install would install a new MBR.  I don't know much about it.  :/

> **drs305 said:**
> Yes it will. You say you need to reinstall Windows for other reasons as well, but for starters if all you need is to get Windows booting again, and you are currently running an ubuntu cd, you can just run the following commands to restore the mbr to point to Windows:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
It will complain about lilo not being completely installed, but forget the messages and only run the above commands. Rebooting should restore the Windows boot.
Unfortunately, the computer does not have internet, so I'd have to download the and compile Lilo manually (unless there is a .deb, which there probably is).  But anyway, yeah, I was looking to reinstall Windows in the first place so this wasn't necessary.

Thanks guys.

---

### Post by e79 on 2011-09-06
No Problem,  Good luck and post back if you have any more issues  :D

Cheers

---

