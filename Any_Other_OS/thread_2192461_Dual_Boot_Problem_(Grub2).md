---
title: "Dual Boot Problem (Grub2)"
date: 2013-12-07
forum: Any Other OS
---

### Post by sredmail on 2013-12-07
Hi,

My Vista / Linux Dual Boot goes into a garbled screen.

I used Boot Repair and it 'repaired' something but I can not boot into Windows or Linux.

   
 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 8Dec2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 410707426 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /BOOTMGR /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       205315080 sectors, but according to the info from 
                       fdisk, it has 210242653 sectors.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

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
    Operating System:  Linux Mint 15 Olivia 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 410706890 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    21,896,594    21,896,532   7 NTFS / exFAT / HPFS
/dev/sda2    *     21,896,595   232,139,248   210,242,654   7 NTFS / exFAT / HPFS
/dev/sda3         232,139,374   488,392,064   256,252,691   f W95 Extended (LBA)
/dev/sda5         399,922,173   410,412,554    10,490,382  82 Linux swap / Solaris
/dev/sda6         410,412,618   488,392,064    77,979,447  83 Linux
/dev/sda7         232,139,376   399,922,109   167,782,734  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4093 MB, 4093640704 bytes
63 heads, 62 sectors/track, 2046 cylinders, total 7995392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,995,391     7,987,200   b W95 FAT32


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 31.4 GB, 31379685376 bytes
8 heads, 32 sectors/track, 239408 cylinders, total 61288448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,760    61,288,447    61,285,688   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA11001510FFD71B                       ntfs       RECOVERY
/dev/sda2        C0D085EDD085E9CC                       ntfs       
/dev/sda5        cd6a1767-79a0-4c5d-b97b-f81cd0f99e78   swap       
/dev/sda6        1f444f67-14f9-462b-8ad7-f24f442b40bd   ext4       
/dev/sda7        f689c421-cb71-4dba-a644-0a89afa64dc1   ext4       
/dev/sdb1        72AD-2013                              vfat       
/dev/sdc1        4850-9927                              vfat       Lexar
/dev/sr0                                                iso9660    Linux Mint 15 Xfce 64-bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/mint/Lexar        vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1f444f67-14f9-462b-8ad7-f24f442b40bd
else
  search --no-floppy --fs-uuid --set=root 1f444f67-14f9-462b-8ad7-f24f442b40bd
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=3
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
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
menuentry 'Linux Mint 15 Xfce 64-bit, 3.8.0-25-generic (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1f444f67-14f9-462b-8ad7-f24f442b40bd
    else
      search --no-floppy --fs-uuid --set=root 1f444f67-14f9-462b-8ad7-f24f442b40bd
    fi
    linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=1f444f67-14f9-462b-8ad7-f24f442b40bd ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-25-generic
}
menuentry 'Linux Mint 15 Xfce 64-bit, 3.8.0-25-generic (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1f444f67-14f9-462b-8ad7-f24f442b40bd
    else
      search --no-floppy --fs-uuid --set=root 1f444f67-14f9-462b-8ad7-f24f442b40bd
    fi
    echo    'Loading Linux 3.8.0-25-generic ...'
    linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=1f444f67-14f9-462b-8ad7-f24f442b40bd ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-25-generic
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
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1f444f67-14f9-462b-8ad7-f24f442b40bd
    else
      search --no-floppy --fs-uuid --set=root 1f444f67-14f9-462b-8ad7-f24f442b40bd
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  1f444f67-14f9-462b-8ad7-f24f442b40bd
    else
      search --no-floppy --fs-uuid --set=root 1f444f67-14f9-462b-8ad7-f24f442b40bd
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Vista (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-FA11001510FFD71B' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  FA11001510FFD71B
    else
      search --no-floppy --fs-uuid --set=root FA11001510FFD71B
    fi
    chainloader +1
}
menuentry 'Windows Vista (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-C0D085EDD085E9CC' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  C0D085EDD085E9CC
    else
      search --no-floppy --fs-uuid --set=root C0D085EDD085E9CC
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=1f444f67-14f9-462b-8ad7-f24f442b40bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cd6a1767-79a0-4c5d-b97b-f81cd0f99e78 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 199.831089973 = 214.566999040  boot/grub/grub.cfg                             1
 200.053540230 = 214.805853184  boot/grub/i386-pc/core.img                     1
 200.042832375 = 214.794355712  boot/vmlinuz-3.8.0-25-generic                  1
 200.042832375 = 214.794355712  vmlinuz                                        1
 195.862957954 = 210.306249728  boot/initrd.img-3.8.0-19-generic               1
 200.120335579 = 214.877574144  boot/initrd.img-3.8.0-25-generic               1
 200.120335579 = 214.877574144  initrd.img                                     1

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/4973/mounts) leaked on lvscan invocation. Parent PID 17815: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-12-08__02h29 ===================
boot-repair version : 3.199~ppa39~raring
boot-sav version : 3.199~ppa39~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa39~raring
boot-repair is executed in live-session (Linux Mint 15 Olivia, olivia, LinuxMint, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet splash -- BOOT_IMAGE=/casper/vmlinuz

=================== os-prober:
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Windows Vista (loader):Windows1:chain
/dev/sda6:Linux Mint 15 Olivia (15):LinuxMint:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="RECOVERY" UUID="FA11001510FFD71B" TYPE="ntfs"
/dev/sda2: UUID="C0D085EDD085E9CC" TYPE="ntfs"
/dev/sda5: UUID="cd6a1767-79a0-4c5d-b97b-f81cd0f99e78" TYPE="swap"
/dev/sda6: UUID="1f444f67-14f9-462b-8ad7-f24f442b40bd" TYPE="ext4"
/dev/sda7: UUID="f689c421-cb71-4dba-a644-0a89afa64dc1" TYPE="ext4"
/dev/sr0: LABEL="Linux Mint 15 Xfce 64-bit" TYPE="iso9660"
/dev/sdb1: UUID="72AD-2013" TYPE="vfat"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda6/etc/grub.d/ :
drwxr-xr-x 2 root root    4096 Apr 25  2013 grub.d
total 84
-rwxr-xr-x 1 root root  7541 Apr  9  2013 00_header
-rwxr-xr-x 1 root root  5974 Apr  9  2013 05_debian_theme
-rwxr-xr-x 1 root root  1183 Oct 23  2011 06_mint_theme
-rwxr-xr-x 1 root root  7500 May 22  2013 10_linux
-rwxr-xr-x 1 root root 10634 Oct  1  2012 10_lupin
-rwxr-xr-x 1 root root 10258 Apr  9  2013 20_linux_xen
-rwxr-xr-x 1 root root  1688 Dec  5  2012 20_memtest86+
-rwxr-xr-x 1 root root 10976 Apr  9  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9  2013 40_custom
-rwxr-xr-x 1 root root   216 Apr  9  2013 41_custom
-rw-r--r-- 1 root root   483 Apr  9  2013 README




=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    BOOTMGR,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD2500BEVS-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  11.2GB  11.2GB  primary   ntfs
2      11.2GB  119GB   108GB   primary   ntfs
3      119GB   250GB   131GB   extended                  lba
7      119GB   205GB   85.9GB  logical   ext4
5      205GB   210GB   5371MB  logical   linux-swap(v1)
6      210GB   250GB   39.9GB  logical   ext4            boot


Model: Generic- Multi-Card (scsi)
Disk /dev/sdb: 4094MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4194kB  4094MB  4089MB  primary  fat32        boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Invalid partition table - recursive partition on /dev/sr0.

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA WDC WD2500BEVS-2;
1:32.3kB:11.2GB:11.2GB:ntfs::;
2:11.2GB:119GB:108GB:ntfs::;
3:119GB:250GB:131GB:::lba;
7:119GB:205GB:85.9GB:ext4::;
5:205GB:210GB:5371MB:linux-swap(v1)::;
6:210GB:250GB:39.9GB:ext4::boot;

BYT;
/dev/sdb:4094MB:scsi:512:512:msdos:Generic- Multi-Card;
1:4194kB:4094MB:4089MB:fat32::boot;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Invalid partition table - recursive partition on /dev/sr0.


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/mint/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mint)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control



=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  172M  1.8G   9% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      383M  984K  382M   1% /run
/dev/sr0       iso9660    950M  950M     0 100% /cdrom
/dev/loop0     squashfs   906M  906M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G   12K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G   80K  1.9G   1% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk     11G  6.6G  3.9G  64% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     98G   89G  9.6G  91% /mnt/boot-sav/sda2
/dev/sda6      ext4        37G  3.4G   32G  10% /mnt/boot-sav/sda6
/dev/sda7      ext4        79G   34G   41G  46% /mnt/boot-sav/sda7
/dev/sdb1      vfat       3.9G  2.2G  1.7G  56% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77ea422a

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    21896594    10948266    7  HPFS/NTFS/exFAT
/dev/sda2        21896595   232139248   105121327    7  HPFS/NTFS/exFAT
/dev/sda3       232139374   488392064   128126345+   f  W95 Ext'd (LBA)
/dev/sda5       399922173   410412554     5245191   82  Linux swap / Solaris
/dev/sda6   *   410412618   488392064    38989723+  83  Linux
/dev/sda7       232139376   399922109    83891367   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4093 MB, 4093640704 bytes
63 heads, 62 sectors/track, 2046 cylinders, total 7995392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef6f0

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7995391     3993600    b  W95 FAT32


adding: log/ (stored 0%)
adding: log/log/ (stored 0%)
adding: log/log/boot-repair (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sdb1/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sdb/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2013-12-08__02h29boot-repair36/sdb/current_mbr.img (deflated 95%)
adding: log/log/2013-12-08__02h29boot-repair36/sda7/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sda6/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sda6/grubenv (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sda2/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sda1/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sda/ (stored 0%)
adding: log/log/2013-12-08__02h29boot-repair36/sda/partition_table.dmp (deflated 53%)
adding: log/log/2013-12-08__02h29boot-repair36/sda/current_mbr.img (deflated 2%)
adding: log/log/2013-12-08__02h29boot-repair36/boot-repair.log (deflated 70%)
adding: log/log/2012-12-02__15h47boot-repair49/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sdb1/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sdb/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-12-02__15h47boot-repair49/sdb/current_mbr.imgSET@_progressbar1.pulse()
(deflated 95%)
adding: log/log/2012-12-02__15h47boot-repair49/sda7/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sda6/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sda6/grubenv (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sda2/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sda1/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sda/ (stored 0%)
adding: log/log/2012-12-02__15h47boot-repair49/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-12-02__15h47boot-repair49/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-12-02__15h47boot-repair49/boot-repair.log (deflated 78%)
adding: log/log/2012-12-02__15h31boot-repair27/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sdb1/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sdb/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-12-02__15h31boot-repair27/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-12-02__15h31boot-repair27/sda7/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sda6/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sda6/grubenv (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sda2/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sda1/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sda/ (stored 0%)
adding: log/log/2012-12-02__15h31boot-repair27/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-12-02__15h31boot-repair27/sda/mbr_before_restoring_mbr.img (deflated 2%)
adding: log/log/2012-12-02__15h31boot-repair27/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-12-02__15h31boot-repair27/RESULTS.txt (deflated 72%)
adding: log/log/2012-12-02__15h31boot-repair27/boot-repair.logb (deflated 63%)
adding: log/log/2012-12-02__15h31boot-repair27/boot-repair.log (deflated 80%)
adding: log/log/2012-12-02__15h04boot-repair27/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sdb1/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sdb/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-12-02__15h04boot-repair27/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-12-02__15h04boot-repair27/sda7/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sda6/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sda6/grubenv (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sda2/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sda1/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sda/ (stored 0%)
adding: log/log/2012-12-02__15h04boot-repair27/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-12-02__15h04boot-repair27/sda/mbr_before_restoring_mbr.img (deflated 2%)
adding: log/log/2012-12-02__15h04boot-repair27/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-12-02__15h04boot-repair27/RESULTS.txt (deflated 72%)
adding: log/log/2012-12-02__15h04boot-repair27/boot-repair.logb (deflated 63%)
adding: log/log/2012-12-02__15h04boot-repair27/boot-repair.log (deflated 80%)
adding: log/log/2012-12-02__14h17boot-repair04/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sdb1/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sdb/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-12-02__14h17boot-repair04/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-12-02__14h17boot-repair04/sda7/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sda6/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sda6/grubenv (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-12-02__14h17boot-repair04/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-12-02__14h17boot-repair04/sda2/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sda1/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sda/ (stored 0%)
adding: log/log/2012-12-02__14h17boot-repair04/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-12-02__14h17boot-repair04/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-12-02__14h17boot-repair04/RESULTS.txt (deflated 73%)
adding: log/log/2012-12-02__14h17boot-repair04/boot-repair.logb (deflated 65%)
adding: log/log/2012-12-02__14h17boot-repair04/boot-repair.log (deflated 81%)
adding: log/log/2012-11-23__14h33boot-repair46/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sdb1/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sdb/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-23__14h33boot-repair46/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-23__14h33boot-repair46/sda7/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sda6/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sda6/grubenv (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sda2/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sda1/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sda/ (stored 0%)
adding: log/log/2012-11-23__14h33boot-repair46/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-11-23__14h33boot-repair46/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-23__14h33boot-repair46/boot-repair.log (deflated 68%)
adding: log/log/2012-11-23__13h14boot-repair10/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sdb1/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sdb/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-23__13h14boot-repair10/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-23__13h14boot-repair10/sda7/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sda6/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sda6/grubenv (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-23__13h14boot-repair10/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-23__13h14boot-repair10/sda2/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sda1/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sda/ (stored 0%)
adding: log/log/2012-11-23__13h14boot-repair10/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-11-23__13h14boot-repair10/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-23__13h14boot-repair10/RESULTS.txt (deflated 72%)
adding: log/log/2012-11-23__13h14boot-repair10/boot-repair.logb (deflated 64%)
adding: log/log/2012-11-23__13h14boot-repair10/boot-repair.log (deflated 79%)
adding: log/log/2012-11-21__18h40boot-repair37/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sdb1/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sdb/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-21__18h40boot-repair37/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-21__18h40boot-repair37/sda7/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sda6/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sda6/grubenv (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-21__18h40boot-repair37/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-21__18h40boot-repair37/sda2/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sda1/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sda/ (stored 0%)
adding: log/log/2012-11-21__18h40boot-repair37/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-11-21__18h40boot-repair37/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-21__18h40boot-repair37/RESULTS.txtSET@_progressbar1.pulse()
(deflated 72%)
adding: log/log/2012-11-21__18h40boot-repair37/boot-repair.logb (deflated 65%)
adding: log/log/2012-11-21__18h40boot-repair37/boot-repair.log (deflated 80%)
adding: log/log/2012-11-21__16h25boot-repair20/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sdb1/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sdb/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-21__16h25boot-repair20/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-21__16h25boot-repair20/sda7/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sda6/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sda6/grubenv (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-21__16h25boot-repair20/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-21__16h25boot-repair20/sda2/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sda1/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sda/ (stored 0%)
adding: log/log/2012-11-21__16h25boot-repair20/sda/partition_table.dmp (deflated 53%)
adding: log/log/2012-11-21__16h25boot-repair20/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-21__16h25boot-repair20/RESULTS.txt (deflated 72%)
adding: log/log/2012-11-21__16h25boot-repair20/boot-repair.logb (deflated 65%)
adding: log/log/2012-11-21__16h25boot-repair20/boot-repair.log (deflated 79%)
adding: log/log/2012-11-21__16h15boot-repair56/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sdc1/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sdc/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sdc/partition_table.dmp (deflated 55%)
adding: log/log/2012-11-21__16h15boot-repair56/sdc/current_mbr.img (deflated 100%)
adding: log/log/2012-11-21__16h15boot-repair56/sdb1/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sdb/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-21__16h15boot-repair56/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-21__16h15boot-repair56/sda7/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sda6/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sda6/grubenv (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sda2/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sda1/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sda/ (stored 0%)
adding: log/log/2012-11-21__16h15boot-repair56/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-21__16h15boot-repair56/sda/mbr_before_restoring_mbr.img (deflated 2%)
adding: log/log/2012-11-21__16h15boot-repair56/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-21__16h15boot-repair56/RESULTS.txt (deflated 73%)
adding: log/log/2012-11-21__16h15boot-repair56/boot-repair.logb (deflated 65%)
adding: log/log/2012-11-21__16h15boot-repair56/boot-repair.log (deflated 82%)
adding: log/log/2012-11-21__16h06boot-repair50/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sdb1/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sdb/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-21__16h06boot-repair50/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-21__16h06boot-repair50/sda7/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sda6/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sda6/grubenv (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-21__16h06boot-repair50/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-21__16h06boot-repair50/sda6/etc_default_grub_old (deflated 43%)
adding: log/log/2012-11-21__16h06boot-repair50/sda2/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sda1/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sda/ (stored 0%)
adding: log/log/2012-11-21__16h06boot-repair50/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-21__16h06boot-repair50/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-21__16h06boot-repair50/RESULTS.txt (deflated 71%)
adding: log/log/2012-11-21__16h06boot-repair50/boot-repair.logb (deflated 64%)
adding: log/log/2012-11-21__16h06boot-repair50/boot-repair.log (deflated 81%)
adding: log/log/2012-11-21__14h15boot-repair05/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sdc1/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sdc/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sdc/partition_table.dmp (deflated 55%)
adding: log/log/2012-11-21__14h15boot-repair05/sdc/current_mbr.img (deflated 100%)
adding: log/log/2012-11-21__14h15boot-repair05/sdb1/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sdb/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-21__14h15boot-repair05/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-21__14h15boot-repair05/sda7/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sda6/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sda6/grubenv (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sda2/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sda1/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sda/ (stored 0%)
adding: log/log/2012-11-21__14h15boot-repair05/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-21__14h15boot-repair05/sda/mbr_before_restoring_mbr.img (deflated 2%)
adding: log/log/2012-11-21__14h15boot-repair05/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-21__14h15boot-repair05/RESULTS.txt (deflated 78%)
adding: log/log/2012-11-21__14h15boot-repair05/boot-repair.logb (deflated 67%)
adding: log/log/2012-11-21__14h15boot-repair05/boot-repair.log (deflated 83%)
adding: log/log/2012-11-21__06h16boot-repair56/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sdb1/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sdb/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-21__06h16boot-repair56/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-21__06h16boot-repair56/sda7/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sda6/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sda6/grubenv (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-21__06h16boot-repair56/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-21__06h16boot-repair56/sda2/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sda1/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sda/ (stored 0%)
adding: log/log/2012-11-21__06h16boot-repair56/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-21__06h16boot-repair56/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-21__06h16boot-repair56/RESULTS.txt (deflated 77%)
adding: log/log/2012-11-21__06h16boot-repair56/boot-repair.logb (deflated 67%)
adding: log/log/2012-11-21__06h16boot-repair56/boot-repair.log (deflated 82%)
adding: log/log/2012-11-20__23h04boot-repair27/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sdb1/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sdb/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-20__23h04boot-repair27/sdb/current_mbr.img (deflated 98%)
adding: log/log/2012-11-20__23h04boot-repair27/sda7/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sda6/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sda6/grubenv (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-20__23h04boot-repair27/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-20__23h04boot-repair27/sda2/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sda1/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sda/ (stored 0%)
adding: log/log/2012-11-20__23h04boot-repair27/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-20__23h04boot-repair27/sda/current_mbr.imgSET@_progressbar1.pulse()
(deflated 2%)
adding: log/log/2012-11-20__23h04boot-repair27/RESULTS.txt (deflated 77%)
adding: log/log/2012-11-20__23h04boot-repair27/boot-repair.logb (deflated 66%)
adding: log/log/2012-11-20__23h04boot-repair27/boot-repair.log (deflated 87%)
adding: log/log/2012-11-20__19h05boot-repair44/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sources.list_after_grubpurge (deflated 69%)
adding: log/log/2012-11-20__19h05boot-repair44/sdb1/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sdb/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-20__19h05boot-repair44/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-20__19h05boot-repair44/sda7/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sda6/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sda6/grub_before_purge (deflated 42%)
adding: log/log/2012-11-20__19h05boot-repair44/sda6/grubenv (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-20__19h05boot-repair44/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-20__19h05boot-repair44/sda2/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sda1/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sda/ (stored 0%)
adding: log/log/2012-11-20__19h05boot-repair44/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-20__19h05boot-repair44/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-20__19h05boot-repair44/RESULTS.txt (deflated 81%)
adding: log/log/2012-11-20__19h05boot-repair44/boot-repair.logb (deflated 78%)
adding: log/log/2012-11-20__19h05boot-repair44/boot-repair.log (deflated 87%)
adding: log/log/2012-11-20__15h41boot-repair56/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sources.list_after_grubpurge (deflated 69%)
adding: log/log/2012-11-20__15h41boot-repair56/sdb1/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sdb/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sdb/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-20__15h41boot-repair56/sdb/current_mbr.img (deflated 95%)
adding: log/log/2012-11-20__15h41boot-repair56/sda7/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sda6/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sda6/grub_before_purge (deflated 42%)
adding: log/log/2012-11-20__15h41boot-repair56/sda6/grubenv (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-20__15h41boot-repair56/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-20__15h41boot-repair56/sda2/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sda1/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sda/ (stored 0%)
adding: log/log/2012-11-20__15h41boot-repair56/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-20__15h41boot-repair56/sda/mbr_before_restoring_mbr.img (deflated 2%)
adding: log/log/2012-11-20__15h41boot-repair56/sda/current_mbr.img (deflated 2%)
adding: log/log/2012-11-20__15h41boot-repair56/RESULTS.txt (deflated 77%)
adding: log/log/2012-11-20__15h41boot-repair56/boot-repair.logb (deflated 66%)
adding: log/log/2012-11-20__15h41boot-repair56/boot-repair.log (deflated 82%)
adding: log/log/2012-11-08__03h07boot-repair51/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sdd1/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sdd/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sdd/partition_table.dmp (deflated 56%)
adding: log/log/2012-11-08__03h07boot-repair51/sdd/current_mbr.img (deflated 98%)
adding: log/log/2012-11-08__03h07boot-repair51/sda7/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sda6/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sda6/grubenv (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sda2/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sda1/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sda/ (stored 0%)
adding: log/log/2012-11-08__03h07boot-repair51/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-08__03h07boot-repair51/sda/mbr_before_restoring_mbr.img (deflated 3%)
adding: log/log/2012-11-08__03h07boot-repair51/sda/current_mbr.img (deflated 3%)
adding: log/log/2012-11-08__03h07boot-repair51/RESULTS.txt (deflated 75%)
adding: log/log/2012-11-08__03h07boot-repair51/boot-repair.logb (deflated 64%)
adding: log/log/2012-11-08__03h07boot-repair51/boot-repair.log (deflated 80%)
adding: log/log/2012-11-06__05h26boot-repair22/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sdb1/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sdb/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sdb/partition_table.dmp (deflated 57%)
adding: log/log/2012-11-06__05h26boot-repair22/sdb/current_mbr.img (deflated 100%)
adding: log/log/2012-11-06__05h26boot-repair22/sda7/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sda6/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sda6/grubenv (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sda6/etc_fstab_old (deflated 46%)
adding: log/log/2012-11-06__05h26boot-repair22/sda6/etc_fstab_new (deflated 46%)
adding: log/log/2012-11-06__05h26boot-repair22/sda2/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sda1/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sda/ (stored 0%)
adding: log/log/2012-11-06__05h26boot-repair22/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-06__05h26boot-repair22/sda/current_mbr.img (deflated 3%)
adding: log/log/2012-11-06__05h26boot-repair22/RESULTS.txt (deflated 75%)
adding: log/log/2012-11-06__05h26boot-repair22/boot-repair.logb (deflated 66%)
adding: log/log/2012-11-06__05h26boot-repair22/boot-repair.log (deflated 80%)
adding: log/log/2012-11-06__04h10boot-repair16/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sdb1/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sdb/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sdb/partition_table.dmp (deflated 57%)
adding: log/log/2012-11-06__04h10boot-repair16/sdb/current_mbr.img (deflated 100%)
adding: log/log/2012-11-06__04h10boot-repair16/sda7/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sda6/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sda6/grub.cfg_old (deflated 85%)
adding: log/log/2012-11-06__04h10boot-repair16/sda2/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sda1/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sda/ (stored 0%)
adding: log/log/2012-11-06__04h10boot-repair16/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-06__04h10boot-repair16/sda/mbr_before_restoring_mbr.img (deflated 3%)
adding: log/log/2012-11-06__04h10boot-repair16/sda/current_mbr.img (deflated 3%)
adding: log/log/2012-11-06__04h10boot-repair16/RESULTS.txt (deflated 75%)
adding: log/log/2012-11-06__04h10boot-repair16/boot-repair.logb (deflated 64%)
adding: log/log/2012-11-06__04h10boot-repair16/boot-repair.log (deflated 82%)
adding: log/log/2012-11-06__00h57boot-repair37/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sdd1/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sdd/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sdd/partition_table.dmp (deflated 57%)
adding: log/log/2012-11-06__00h57boot-repair37/sdd/current_mbr.img (deflated 100%)
adding: log/log/2012-11-06__00h57boot-repair37/sda7/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sda6/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sda2/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sda1/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sda/ (stored 0%)
adding: log/log/2012-11-06__00h57boot-repair37/sda/partition_table.dmp (deflated 54%)
adding: log/log/2012-11-06__00h57boot-repair37/sda/current_mbr.img (deflated 22%)
adding: log/log/2012-11-06__00h57boot-repair37/boot-repair.log (deflated 69%)
adding: log/2013-12-08__02h29boot-repair36/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sdb1/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sdb/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sdb/partition_table.dmp (deflated 56%)
adding: log/2013-12-08__02h29boot-repair36/sdb/current_mbr.img (deflated 95%)
adding: log/2013-12-08__02h29boot-repair36/sda7/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sda6/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sda6/grubenv (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sda2/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sda1/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sda/ (stored 0%)
adding: log/2013-12-08__02h29boot-repair36/sda/partition_table.dmp (deflated 53%)
adding: log/2013-12-08__02h29boot-repair36/sda/current_mbr.img (deflated 2%)
adding: log/2013-12-08__02h29boot-repair36/boot-repair.log
zip warning:  file size changed while zipping log/2013-12-08__02h29boot-repair36/boot-repair.log
(deflated 83%)

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda6 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Custom-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair will be performed: unhide-bootmenu-3s   fix-windows-boot


Quantity of real Windows: 2
Unhide GRUB boot menu in sda6/etc/default/grub
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.

Unhide GRUB boot menu in sda6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by oldfred on 2013-12-08
Moved to OtherOS since not Ubuntu.

You have grub installed to PBR - partition boot sectors. You should fix sda1 with this, but you have boot flag on sda2 and it looks like it needs chkdsk. Use your Windows repairCD or flash drive to run chkdsk if f8 does not get you to a repair console.
Once you get Windows booting from sda, you need to reinstall grub2 to sda for you Mint install in sda6. Run Boot-Repair to do that.  Grub only boots working Windows, so best to resolve Windows issues first.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Also it looks like your Windows is full. When Windows gets below 10% free space it becomes very slow and a defrag may take forever as it has no working room. Best to have 30% free space in NTFS partitions for Windows not to slow down.

---

