---
title: "Grub 2 Doesn't recognize/allow booting up into Windows 7, even if installed."
date: 2013-08-15
forum: Any Other OS
---

### Post by TheEliteNoob on 2013-08-15
So, I had another thread and got windows 7 and ubuntu installed on seperate hard drives. However when I boot up it automatically takes me to grub like it should, except grub doesn't have the entry for windows 7, which is on the hdd (sdb) and linux on the ssd (sda) and (/home on the hdd). And making a custom entry doesn't work. Neither did update-grub or os-prober.

Boot info script:
```

                   Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/debian/grubx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Debian GNU/Linux jessie/sid
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sdb2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


sdb3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1    46,905,263    46,905,263  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       999,423       997,376 EFI System partition
/dev/sda2         999,424    34,611,199    33,611,776 Data partition (Linux)
/dev/sda3      34,611,200    46,903,295    12,292,096 Swap partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2         929,523,712 1,953,521,663 1,023,997,952   7 NTFS / exFAT / HPFS
/dev/sdb3             208,894   929,523,711   929,314,818   5 Extended
/dev/sdb5             208,896   929,523,711   929,314,816  83 Linux




Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1    *          2,048    31,266,815    31,264,768   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        C305-3C30                              vfat       
/dev/sda2        62a90ee6-118a-4675-839b-e9bd8e18794b   ext4       
/dev/sda3        3e9b4d37-2485-4b8e-882a-f821eda1616f   swap       
/dev/sdb1        4C429DF5429DE3CC                       ntfs       System Reserved
/dev/sdb2        E08EAA5D8EAA2C4A                       ntfs       
/dev/sdb5        d7e6a98c-7bd0-4e26-b1b1-e023a12eb000   ext4       
/dev/sdc1        B4AA-1FD6                              vfat       HYRULE


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




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


function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}


insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root 62a90ee6-118a-4675-839b-e9bd8e18794b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root 62a90ee6-118a-4675-839b-e9bd8e18794b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 3.9-1-amd64' --class debian --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 62a90ee6-118a-4675-839b-e9bd8e18794b
    echo    'Loading Linux 3.9-1-amd64 ...'
    linux    /boot/vmlinuz-3.9-1-amd64 root=UUID=62a90ee6-118a-4675-839b-e9bd8e18794b ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.9-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.9-1-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 62a90ee6-118a-4675-839b-e9bd8e18794b
    echo    'Loading Linux 3.9-1-amd64 ...'
    linux    /boot/vmlinuz-3.9-1-amd64 root=UUID=62a90ee6-118a-4675-839b-e9bd8e18794b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.9-1-amd64
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
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


=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=62a90ee6-118a-4675-839b-e9bd8e18794b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=C305-3C30  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sdb5 during installation
UUID=d7e6a98c-7bd0-4e26-b1b1-e023a12eb000 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=3e9b4d37-2485-4b8e-882a-f821eda1616f none            swap    sw              0       0
/dev/sdc1       /media/usb0     auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.9-1-amd64                    2
               =                boot/vmlinuz-3.9-1-amd64                       1
               =                vmlinuz                                        1


=========================== sdc1/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try elementary OS without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install elementary OS" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


=================== sdc1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/grub.cfg                             1


=============================== StdErr Messages: ===============================


awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

I can still boot into windows if I go into the boot menu and choose the HDD instead of letting it boot into grub with the ssd.

---

### Post by oldfred on 2013-08-15
It looks like you have Debian installed in UEFI mode and Windows in BIOS mode. Both systems must be in same boot mode to dual boot.
The only way to boot is the way you say. Go into UEFI and turn it on to boot Debian, and then go into BIOS and change to BIOS/CSM mode to boot Windows. Some systems will auto switch when in CSM mode which you may have if you just select which system to boot.

UEFI and BIOS boot modes are not compatible as they use different drivers and configurations. So you cannot start booting in UEFI mode and switch to BIOS as UEFI has written system data to hard drive for booting.

---

### Post by TheEliteNoob on 2013-08-15
> **oldfred said:**
> It looks like you have Debian installed in UEFI mode and Windows in BIOS mode. Both systems must be in same boot mode to dual boot.
The only way to boot is the way you say. Go into UEFI and turn it on to boot Debian, and then go into BIOS and change to BIOS/CSM mode to boot Windows. Some systems will auto switch when in CSM mode which you may have if you just select which system to boot.

UEFI and BIOS boot modes are not compatible as they use different drivers and configurations. So you cannot start booting in UEFI mode and switch to BIOS as UEFI has written system data to hard drive for booting.
Hmm, This is a lenovo u410 ultrabook btw, and I'm willing to reinstall debian as it's a minimal netinstall and i haven't done anything with it yet. So how would I reinstall debian but in BIOS mode instead? I really want/need to make this work...

---

### Post by oldfred on 2013-08-16
Moved to Other OS as it is Debian not Ubuntu.

I do not know Debian, but with Ubuntu how you boot installer is how it installs. Or if you boot in BIOS mode it installs in BIOS mode. And you have to select that from UEFI/BIOS menu.

---

### Post by TheEliteNoob on 2013-08-16
I don't know how to do that, I just plugged in my usb and let it run, Not really sure how i can choose this...

---

### Post by oldfred on 2013-08-16
It may be settings in UEFI and then which option you choose to boot from.
With those systems with secure boot only secure boot options are shown. 
But some have a CSM setting that will boot UEFI mode if efi folder found and then will boot CSM/BIOS is efi not found. Not sure how you might control those systems. Should then have CSM only setting.

---

