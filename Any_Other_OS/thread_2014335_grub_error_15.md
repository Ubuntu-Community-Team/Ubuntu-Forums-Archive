---
title: "grub error 15"
date: 2012-07-01
forum: Any Other OS
---

### Post by bth73 on 2012-07-01
Just ran rescatux again after posting this, and did not fix, instead of grub 15 error, it got past that and then gave me "the disk drive for /windows/c is not ready yet or is not present - press s to skip or m for manual recovery". 
I then ran the automatic fix from a Suse 11.2 disk. It had a lot of errors through the process, but seams to have fixed the boot problem. For now.

This started with a dvd swap. Gigabyte GA K8NS 939 ultra mother board, has 4channel pata, and 4channel sata. 2 Sata HD, 1 pata HD, 1 pata dvd, 1 sata dvd. Tried to replace pata dvd with new sata, but could not cdrom boot through sata channel, so, I put the pata dvd back, then grub 15 error. Been trying fixes including Suse disk. After aborted Suse fix, it booted again. Then last night, I removed the 3 HD's and put a different empty 500gig HD in and installed Mint 13 on it. I then took it out and replaced the original 3 HD's and now get the same grub 15 error. Tried fsck, and replace/install grub with the rescatux cd, but no fix.
750 gig pata/fat 32 drive should not have grub on it and I don't know how it got there.
sda6 or sdb6 was a dual-boot install of mint9 to try fixing grub/boot and will resize and wipe out later. There is a unallocated 100mb at the front of sdb1, (main mint 9 install).
 
This is a semi-automated message generated from [Rescatux live cd]("http://www.supergrubdisk.org").
My description of my system is:
My system has Mint9 operating system with 3 hard disks
My problem is:
I am unable to do something as easy as...boot grub error 15
I join the Rescatux output for bootinfoscript_log.txt :
```

                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on boot 
    drive #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of t
Finished. The results are in the file "stdout"
located in "/dev/".

  looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 9 Isadora
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 9 Isadora
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,465,144,064 1,465,144,002   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,857,143,087 1,857,141,040  83 Linux
/dev/sdb2       1,857,144,830 1,953,523,711    96,378,882   5 Extended
/dev/sdb5       1,935,409,152 1,953,523,711    18,114,560  82 Linux swap / Solaris
/dev/sdb6       1,857,144,832 1,932,105,727    74,960,896  83 Linux
/dev/sdb7       1,932,107,776 1,935,398,911     3,291,136  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B0FF-1537                              vfat       
/dev/sdb1        7ca8ad00-2177-45c8-bcee-48e18571da58   ext4       
/dev/sdb5        d7739a58-d4ca-46a4-a899-499ed3abd682   swap       
/dev/sdb6        5a9f409a-09d3-45b4-9aa6-10e60b14713d   ext4       
/dev/sdb7        47e12a78-9b66-412c-9f46-4ca4e86a6604   swap       
/dev/sdc         8607e428-757e-4a34-8c4a-38b8e2fdf45a   ext4       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr1         /live/image              iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=12
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
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
menuentry "Linux Mint 9, 2.6.32-41-generic (/dev/sda1)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry "Linux Mint 9, 2.6.32-41-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	echo	'Loading Linux 2.6.32-41-generic ...'
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry "Linux Mint 9, 2.6.32-40-generic (/dev/sda1)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux	/boot/vmlinuz-2.6.32-40-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-40-generic
}
menuentry "Linux Mint 9, 2.6.32-40-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	echo	'Loading Linux 2.6.32-40-generic ...'
	linux	/boot/vmlinuz-2.6.32-40-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-40-generic
}
menuentry "Linux Mint 9, 2.6.32-38-generic (/dev/sda1)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry "Linux Mint 9, 2.6.32-38-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	echo	'Loading Linux 2.6.32-38-generic ...'
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry "Linux Mint 9, 2.6.32-37-generic (/dev/sda1)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry "Linux Mint 9, 2.6.32-37-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda1)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5a9f409a-09d3-45b4-9aa6-10e60b14713d ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5a9f409a-09d3-45b4-9aa6-10e60b14713d ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
# / was on /dev/sda1 during installation
# swap was on /dev/sda5 during installation
UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 /                    ext4       defaults              1 1
/dev/disk/by-id/ata-ST3500630AS_9QG730MR-part1 /data1               auto       noauto,user           0 0
/dev/disk/by-id/ata-ST3750640NA_P_3QD16417-part1 /windows/C           vfat       users,gid=users,umask=0002,iocharset=iso8859-15 0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
/dev/disk/by-id/ata-WDC_WD1001FALS-00J7B0_WD-WMATV6747687-part5 swap                 swap       default               0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.32-21-generic              1
            ?? = ??             boot/initrd.img-2.6.32-37-generic              1
            ?? = ??             boot/initrd.img-2.6.32-38-generic              2
            ?? = ??             boot/initrd.img-2.6.32-40-generic              2
            ?? = ??             boot/initrd.img-2.6.32-41-generic              1
            ?? = ??             boot/vmlinuz-2.6.32-21-generic                 1
            ?? = ??             boot/vmlinuz-2.6.32-37-generic                 1
            ?? = ??             boot/vmlinuz-2.6.32-38-generic                 1
            ?? = ??             boot/vmlinuz-2.6.32-40-generic                 1
            ?? = ??             boot/vmlinuz-2.6.32-41-generic                 1
            ?? = ??             initrd.img                                     1
            ?? = ??             initrd.img.old                                 2
            ?? = ??             vmlinuz                                        1
            ?? = ??             vmlinuz.old                                    1

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
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
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5a9f409a-09d3-45b4-9aa6-10e60b14713d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda6) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5a9f409a-09d3-45b4-9aa6-10e60b14713d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5a9f409a-09d3-45b4-9aa6-10e60b14713d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-41-generic (/dev/sda1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-41-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Linux Mint 9, 2.6.32-41-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-41-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single
	initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Linux Mint 9, 2.6.32-40-generic (/dev/sda1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-40-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-40-generic
}
menuentry "Linux Mint 9, 2.6.32-40-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-40-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single
	initrd /boot/initrd.img-2.6.32-40-generic
}
menuentry "Linux Mint 9, 2.6.32-38-generic (/dev/sda1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Linux Mint 9, 2.6.32-38-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Linux Mint 9, 2.6.32-37-generic (/dev/sda1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Linux Mint 9, 2.6.32-37-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7ca8ad00-2177-45c8-bcee-48e18571da58
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7ca8ad00-2177-45c8-bcee-48e18571da58 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

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
UUID=5a9f409a-09d3-45b4-9aa6-10e60b14713d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=47e12a78-9b66-412c-9f46-4ca4e86a6604 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.32-21-generic              1
            ?? = ??             boot/vmlinuz-2.6.32-21-generic                 1
            ?? = ??             initrd.img                                     1
            ?? = ??             vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  4c 98 91 be 71 21 e6 d8  34 de 44 d8 2b 03 a7 c2  |L...q!..4.D.+...|
00000010  9e 5a 19 1f 94 0a ad c7  a6 ba 44 f0 a8 45 c9 71  |.Z........D..E.q|
00000020  a3 29 de 7c 42 b1 4b 5c  3a c3 48 4d c7 08 f9 86  |.).|B.K\:.HM....|
00000030  e8 89 53 61 b5 38 d2 8e  a7 7c 5c e3 6f 11 73 31  |..Sa.8...|\.o.s1|
00000040  13 65 07 c5 5a f1 0f 40  69 e3 50 16 15 fe 99 59  |.e..Z..@i.P....Y|
00000050  93 07 1c 2d 4e ad 7c 19  8a 73 af 38 08 4f 4f 15  |...-N.|..s.8.OO.|
00000060  e9 3e 06 58 46 08 3d 56  e2 79 d2 0d c6 46 45 6e  |.>.XF.=V.y...FEn|
00000070  e1 e0 ab b5 02 b2 6e bc  f8 89 91 bc 5b e2 71 0f  |......n.....[.q.|
00000080  4c d3 6f f8 72 78 8d c1  5f 7b c2 83 61 5f 22 3a  |L.o.rx.._{..a_":|
00000090  34 3c 08 75 7f dc de 30  30 7f 7a 4e 8a 93 9d 0a  |4<.u...00.zN....|
000000a0  5a cb a4 61 99 3c 7b 82  a2 46 72 57 b8 f0 8b a5  |Z..a.<{..FrW....|
000000b0  2a 7e c6 75 f6 d5 46 4d  85 3f 3f 37 0a f8 6b f8  |*~.u..FM.??7..k.|
000000c0  90 63 f0 39 5b 0c 8b a7  94 2b fe 56 e7 48 e6 d8  |.c.9[....+.V.H..|
000000d0  6c d0 53 4b 87 02 cc 8d  f4 64 5f e5 5f 6f 39 84  |l.SK.....d_._o9.|
000000e0  20 c6 9a 27 02 9f 4d e7  76 4c 2c 44 f6 b6 0e f0  | ..'..M.vL,D....|
000000f0  ff d5 33 d9 80 11 ee 43  47 04 76 c1 15 3d fc 80  |..3....CG.v..=..|
00000100  67 a4 5f 4b 05 ce 02 9b  3f d1 13 f8 bb 85 de e3  |g._K....?.......|
00000110  10 82 df 6c a0 37 39 e9  b3 4c 61 93 a2 3f bb 8d  |...l.79..La..?..|
00000120  0b c9 ef 67 48 8a 09 3d  cd 32 23 cf ee b1 43 12  |...gH..=.2#...C.|
00000130  7b 75 b4 c2 f2 61 1e 3a  5a 96 98 1c 2c 48 b4 5d  |{u...a.:Z...,H.]|
00000140  29 1e 73 4c e7 4e 85 1e  9e ae 7e e1 3d 3d d5 c6  |).sL.N....~.==..|
00000150  47 46 13 b8 f9 d1 56 64  e8 22 d6 96 60 75 dd da  |GF....Vd."..`u..|
00000160  c7 2b fa 70 42 f0 e9 b7  bc 14 eb ab b1 0e 1d f2  |.+.pB...........|
00000170  c8 70 53 da 99 aa 98 dd  9a c4 dc 5b 09 96 0a 44  |.pS........[...D|
00000180  7d 0b d9 6c 51 dd 6e 56  d6 05 8f 7c 99 a2 5f c6  |}..lQ.nV...|.._.|
00000190  82 71 1f c6 fa 37 19 33  8c 53 d8 d7 13 8e 82 76  |.q...7.3.S.....v|
000001a0  f2 2f d4 27 ec 38 15 f4  82 7e 8b c7 74 d0 66 22  |./.'.8...~..t.f"|
000001b0  61 14 3a c1 b9 fe 78 54  23 fa be 56 0d d1 00 fe  |a.:...xT#..V....|
000001c0  ff ff 82 fe ff ff 02 38  aa 04 00 68 14 01 00 fe  |.......8...h....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 d0 77 04 00 00  |............w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```
Thank you very much for your help!
The perpetual noob, Bt

---

### Post by Perfect Storm on 2012-07-02
Moved to Other OS/Distro Talk.

---

### Post by oldfred on 2012-07-02
Only grub legacy reports error numbers and often error 15 is some conflict between grub legacy & grub2. But that says you must be booting from sda the FAT drive.

The boot script did not fill out all the info on the MBR of sdb like it normally does. So I cannot tell if the grub2 in sdb is correct or which install sdb1 or sdb6 is the one booting or trying to boot.

Have you tried booting sdb?

You can use a liveCD to reinstall grub2's boot loader to the MBR. Does rescatux get you booted into one of your systems. That it what it usually does with a broken system. If you can boot you can just reinstall grub2's boot loader:

sudo grub-install /dev/sdb

If you cannot boot, change example with sda5 to sdb1 or sdb6 for which ever install you want to boot from:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

