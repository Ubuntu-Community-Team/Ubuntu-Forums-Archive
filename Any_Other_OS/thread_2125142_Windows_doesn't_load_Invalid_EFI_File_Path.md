---
title: "Windows doesn't load: Invalid EFI File Path"
date: 2013-03-13
forum: Any Other OS
---

### Post by Cuithinien on 2013-03-13
I installed Linux Mint, and in the process removed Windows 7 (the C:\ drive was corrupted). I had a backup, fortunately, so I reformatted the drive and restored the backup. Linux Mint recognizes the drive and all its files, GParted says it's a-ok, and GRUB recognizes it as an operating system. But when I try to boot to Windows 7, it spits out "Invalid EFI file path". Now, this seemed similar to [this thread's situation]("http://ubuntuforums.org/showthread.php?t=1904422"), so I ran bootinfoscript (post 4), which gave this:
```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/burg.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/linuxmint/grubx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 14 Nadia
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/burg/core.img


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb3 has 
                       40550399 sectors, but according to the info from 
                       fdisk, it has 40963823 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   125,045,423   125,045,423  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       195,346       195,313 EFI System partition
/dev/sda2         195,347   108,474,643   108,279,297 Data partition (Windows/Linux)
/dev/sda3     108,474,644   125,045,374    16,570,731 Swap partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          1,979 1,424,185,343 1,424,183,365   7 NTFS / exFAT / HPFS
/dev/sdb3       1,424,185,344 1,465,149,167    40,963,824  12 Compaq diagnostics




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        1C97-E85B                              vfat       
/dev/sda2        aadfc00d-845a-4085-a610-a77d4c8a0303   ext4       
/dev/sda3        a534fe8a-1366-47e1-bb4a-84ac33edc986   swap       
/dev/sdb1        49EF34B75D4CF4DA                       ntfs       
/dev/sdb3        8AFADDE7FADDCF95                       ntfs       LENOVO_PART


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb3        /media/LENOVO_PART       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)




=========================== sda2/boot/grub/grub.cfg: ===========================


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
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  aadfc00d-845a-4085-a610-a77d4c8a0303
else
  search --no-floppy --fs-uuid --set=root aadfc00d-845a-4085-a610-a77d4c8a0303
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
menuentry 'Linux Mint 14 Cinnamon 64-bit, 3.5.0-17-generic (/dev/sda2)' --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  aadfc00d-845a-4085-a610-a77d4c8a0303
    else
      search --no-floppy --fs-uuid --set=root aadfc00d-845a-4085-a610-a77d4c8a0303
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=aadfc00d-845a-4085-a610-a77d4c8a0303 ro   
    initrd    /boot/initrd.img-3.5.0-17-generic
}
menuentry 'Linux Mint 14 Cinnamon 64-bit, 3.5.0-17-generic (/dev/sda2) -- recovery mode' --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  aadfc00d-845a-4085-a610-a77d4c8a0303
    else
      search --no-floppy --fs-uuid --set=root aadfc00d-845a-4085-a610-a77d4c8a0303
    fi
    echo    'Loading Linux 3.5.0-17-generic ...'
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=aadfc00d-845a-4085-a610-a77d4c8a0303 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-17-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-49EF34B75D4CF4DA' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  49EF34B75D4CF4DA
    else
      search --no-floppy --fs-uuid --set=root 49EF34B75D4CF4DA
    fi
    chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sdb3)' --class windows --class os $menuentry_id_option 'osprober-chain-8AFADDE7FADDCF95' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  8AFADDE7FADDCF95
    else
      search --no-floppy --fs-uuid --set=root 8AFADDE7FADDCF95
    fi
    drivemap -s (hd0) ${root}
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


=========================== sda2/boot/burg/burg.cfg: ===========================


--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#


### BEGIN /etc/burg.d/00_header ###
set theme_name=burg
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
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
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set aadfc00d-845a-4085-a610-a77d4c8a0303
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###


### BEGIN /etc/burg.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 3.5.0-17-generic' --class linuxmint --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aadfc00d-845a-4085-a610-a77d4c8a0303
    echo    'Loading Linux 3.5.0-17-generic ...'
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=aadfc00d-845a-4085-a610-a77d4c8a0303 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-17-generic
}
menuentry 'LinuxMint GNU/Linux, with Linux 3.5.0-17-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aadfc00d-845a-4085-a610-a77d4c8a0303
    echo    'Loading Linux 3.5.0-17-generic ...'
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=aadfc00d-845a-4085-a610-a77d4c8a0303 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-17-generic
}
### END /etc/burg.d/10_linux ###


### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 49ef34b75d4cf4da
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb3)" --class windows --class os {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 8afadde7faddcf95
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/burg.d/30_os-prober ###


### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------


=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda2 :
UUID=aadfc00d-845a-4085-a610-a77d4c8a0303    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=1C97-E85B    /boot/efi    vfat    defaults    0    1
#Entry for /dev/sdb3 :
UUID=8AFADDE7FADDCF95    /media/LENOVO_PART    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb1 :
UUID=49EF34B75D4CF4DA    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda3 :
UUID=a534fe8a-1366-47e1-bb4a-84ac33edc986    none    swap    sw    0    0




--------------------------------------------------------------------------------


====================== sda2/boot/extlinux/extlinux.conf: =======================


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


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


  44.359673977 = 47.630837248   boot/burg/burg.cfg                             2
   4.222077847 = 4.533421568    boot/burg/core.img                             1
  44.447198391 = 47.724815872   boot/grub/grub.cfg                             1
  44.302648067 = 47.569606144   boot/initrd.img-3.5.0-17-generic               1
   4.226899624 = 4.538598912    boot/vmlinuz-3.5.0-17-generic                  1
  44.302648067 = 47.569606144   initrd.img                                     1
  44.302648067 = 47.569606144   initrd.img.old                                 1
   4.226899624 = 4.538598912    vmlinuz                                        1


================= sda2: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


   4.221810818 = 4.533134848    boot/extlinux/chain.c32                        1
   4.273004055 = 4.588103168    boot/extlinux/extlinux.conf                    1


============== sda2: Version of COM32(R) files used by Syslinux: ===============


 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

```
I lost the thread (no pun intended:)) from there. Any ideas?

---

### Post by oldfred on 2013-03-13
You have mixed UEFI and BIOS boot.

Windows on sdb is configured for BIOS boot and MBR(msdos) partitioning.
Your sda has an efi partition with gpt partitioning and is trying to use UEFI to boot.
Ubuntu will boot from gpt partitioned drives in BIOS mode, but needs a tiny 1MB unformatted bios_grub partition not the efi partition. But how you install is determined by how you boot installer. If you boot installer in UEFI mode it installs in UEFI.

Windows only boots in UEFI mode from gpt partitioned drives.
Windows boots from MBR drives in BIOS or legacy mode.

---

### Post by Cuithinien on 2013-03-14
Thanks for the response. So, from what I understand, my HDD and SSD are formatted differently and are therefore incompatible?
More importantly, what can I do? If I reformat the drive, how do I avoid this error again?

---

### Post by oldfred on 2013-03-14
While I now prefer gpt partitioning, you need to convert your SSD from gpt back to MBR and reinstall Linux in BIOS/MBR mode. With both systems is BIOS mode you should not have any issues.

How you boot installer is how it installs, so be sure to boot in Legacy/BIOS/CSM mode not UEFI mode to install Linux.

You may be able to convert, but that may not be easier than a new install?

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by Cuithinien on 2013-03-14
Thanks! I'll do that. But if possible, can you explain (or give a link that explains) what exactly UEFI, MBR, GPT, CSM, and BIOS are? I'm confused.
P.S. On second thought, should I post this in the beginners' forum?

---

### Post by oldfred on 2013-03-14
Some links:
gpt(GUID) and MBR(msdos) are two ways to partition a drive.
The MBR is the first sector of a hard drive that a BIOS uses. BIOS determines hardware and then jumps to MBR to start to boot a computer.
UEFI is a new replacement for BIOS, but has a BIOS mode also also known as CSM. UEFI looks into efi partition for more boot code.
 Compatibility Support Module (CSM), which emulates a BIOS mode

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

More technical:
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by Cuithinien on 2013-03-15
Thanks. I used gdisk to change /dev/sdb (the Windows disk) to GPT, but the same error still happens. My BIOS is UEFI-capable, and Windows 7 should boot from a GPT disk. But that doesn't seem to have anything to do with the "Invalid EFI file path" error. Ideas?

---

### Post by oldfred on 2013-03-15
You cannot just convert Windows to UEFI boot. Not sure of all the details but it has to have some unformatted space in the partition just before the main Windows install and you have to have an efi partition, usually first, but many Windows installs have a repair partition or recovery partition first. It is a lot of change. It may be easier just to reinstall in UEFI mode. You have to boot installer in UEFI mode.

Even with Ubuntu you have to convert from BIOS boot to UEFI boot. It primarily is changing boot loader from grub-pc(BIOS) to grub-efi (UEFI) and editing fstab to use efi partition. 

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

---

