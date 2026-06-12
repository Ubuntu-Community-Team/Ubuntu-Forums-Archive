---
title: "Windows loads automaticall after install; no grub"
date: 2011-07-26
forum: Any Other OS
---

### Post by orrymr on 2011-07-26
Hi all
So, I've got Windows 7 on 240gig SSD. I want to install Mint 11, Katya. I've downloaded it (md5sum is correct), I've partitioned my hard drive and attempted the install. Everything seemed to be going well. I then restarted in order to complete the installation, but when I did so, Windows 7 booted automatically. Grub doesn't seem to be working. I'm not sure where to go from here. Also, I'm now working from the live cd, and when I go to the partition where I wanted to install Mint, my home folder is empty. Though this could just be because the installation hasn't finished properly (everything else seems to be there).  

Thanks

---

### Post by mips on 2011-07-26
Just to clarify, did you install mint on the SSD or on another hard drive?

---

### Post by orrymr on 2011-07-26
On the SSD; I've got Windows installed on the SSD as well.

---

### Post by mips on 2011-07-26
Was grub installed and where did you specify grub to be installed?

Maybe try again.

---

### Post by ajgreeny on 2011-07-26
It will help if you click on the Boot-info-script link in my signature and follow the instructions to download, run, and then post the RESULTS.txt file it produces back here in code tags (the # in toolbar of the reply entry box).

---

### Post by LooneyLoonz on 2011-07-26
Hi guys,

So the OP is a friend of mine who came over to install mint on my machine. We have been unsuccessful. Just to give some more detail before I post the results.txt.

I have a OCZ Vertex 3 240gb SSD, this drive is my main OS drive (at the moment windows 7).

I have 6 other hdds that I use for all my data, so the SSD is used only for OS installations.

My SSD drive has been partitioned, so that I can install Linux Mint 11 as a dual boot with windows 7.

The installation went fine (no errors nothing). When I rebooted the machine, instead of getting to the grub menu where I can choose which OS to boot, it simply starts loading windows 7.

From what I can see, mint is there, however the grub menu simply wont load, perhaps we didnt install properly.

Here is the results.txt, hopefully someone will be able to help me solve this issue.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 5b326be5-276a-43b7-84e7-7b2ffaed69fe root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sde5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdf2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdf3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             62 1,953,520,064 1,953,520,003   f W95 Extended (LBA)
/dev/sda5                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1              16,129 3,907,024,064 3,907,007,936   f W95 Extended (LBA)
/dev/sdc5              16,192 3,907,024,064 3,907,007,873   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               1,985 1,953,521,663 1,953,519,679   f W95 Extended (LBA)
/dev/sdd5               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               1,985 2,930,272,255 2,930,270,271   f W95 Extended (LBA)
/dev/sde5               2,048 2,930,272,255 2,930,270,208   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdf2             206,848   390,528,936   390,322,089   7 NTFS / exFAT / HPFS
/dev/sdf3         390,529,022   468,860,927    78,331,906   5 Extended
/dev/sdf5         390,529,024   456,296,447    65,767,424  83 Linux
/dev/sdf6         456,298,496   468,860,927    12,562,432  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        F62E6E902E6E49A7                       ntfs       Storage 5
/dev/sdb1        545E7D615E7D3D34                       ntfs       Mass TB
/dev/sdc5        01CC0BBB1D97A890                       ntfs       Storage 4
/dev/sdd5        F20037C800379319                       ntfs       Storage 1
/dev/sde5        DA6435F16435D0CD                       ntfs       Storage 2
/dev/sdf1        B8EE429CEE425334                       ntfs       System Reserved
/dev/sdf2        044E47C04E47A96E                       ntfs       
/dev/sdf5        c4552ee1-7895-480a-aeea-11407b068716   ext4       
/dev/sdf6        bbfec781-1b32-4ea6-bfb6-34027f8f9a90   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdf5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdf,msdos5)'
search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdf,msdos5)'
search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
set locale_dir=($root)/boot/grub/locale
set lang=en_ZA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdf,msdos5)'
search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdf,msdos5)'
search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
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
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdf5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4552ee1-7895-480a-aeea-11407b068716 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdf5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4552ee1-7895-480a-aeea-11407b068716 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
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
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdf,msdos5)'
    search --no-floppy --fs-uuid --set=root c4552ee1-7895-480a-aeea-11407b068716
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdf1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdf,msdos1)'
    search --no-floppy --fs-uuid --set=root B8EE429CEE425334
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

=============================== sdf5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf5 during installation
UUID=c4552ee1-7895-480a-aeea-11407b068716 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf6 during installation
UUID=bbfec781-1b32-4ea6-bfb6-34027f8f9a90 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdf5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 202.457424164 = 217.387003904  boot/grub/core.img                             1
 190.420120239 = 204.462047232  boot/grub/grub.cfg                             1
 186.875000000 = 200.655503360  boot/initrd.img-2.6.38-8-generic               2
 202.351566315 = 217.273339904  boot/vmlinuz-2.6.38-8-generic                  1
 186.875000000 = 200.655503360  initrd.img                                     2
 202.351566315 = 217.273339904  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  05 00 4e 00 54 00 4c 00  44 00 52 00 04 00 24 00  |..N.T.L.D.R...$.|
00000010  49 00 33 00 30 00 00 e0  00 00 00 30 00 00 00 00  |I.3.0......0....|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 eb 12  90 90 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 8c c8 8e d8 c1 e0  |................|
00000070  04 fa 8b e0 fb e8 03 fe  66 0f b7 06 0b 00 66 0f  |........f.....f.|
00000080  b6 1e 0d 00 66 f7 e3 66  a3 4e 02 66 8b 0e 40 00  |....f..f.N.f..@.|
00000090  80 f9 00 0f 8f 0e 00 f6  d9 66 b8 01 00 00 00 66  |.........f.....f|
000000a0  d3 e0 eb 08 90 66 a1 4e  02 66 f7 e1 66 a3 52 02  |.....f.N.f..f.R.|
000000b0  66 0f b7 1e 0b 00 66 33  d2 66 f7 f3 66 a3 56 02  |f.....f3.f..f.V.|
000000c0  e8 71 04 66 8b 0e 4a 02  66 89 0e 22 02 66 03 0e  |.q.f..J.f..".f..|
000000d0  52 02 66 89 0e 26 02 66  03 0e 52 02 66 89 0e 2a  |R.f..&.f..R.f..*|
000000e0  02 66 03 0e 52 02 66 89  0e 3a 02 66 03 0e 52 02  |.f..R.f..:.f..R.|
000000f0  66 89 0e 42 02 66 b8 90  00 00 00 66 8b 0e 22 02  |f..B.f.....f..".|
00000100  e8 5f 09 66 0b c0 0f 84  57 fe 66 a3 2e 02 66 b8  |._.f....W.f...f.|
00000110  a0 00 00 00 66 8b 0e 26  02 e8 46 09 66 a3 32 02  |....f..&..F.f.2.|
00000120  66 b8 b0 00 00 00 66 8b  0e 2a 02 e8 34 09 66 a3  |f.....f..*..4.f.|
00000130  36 02 66 a1 2e 02 66 0b  c0 0f 84 24 fe 67 80 78  |6.f...f....$.g.x|
00000140  08 00 0f 85 1b fe 67 66  8d 50 10 67 03 42 04 67  |......gf.P.g.B.g|
00000150  66 0f b6 48 0c 66 89 0e  62 02 67 66 8b 48 08 66  |f..H.f..b.gf.H.f|
00000160  89 0e 5e 02 66 a1 5e 02  66 0f b7 0e 0b 00 66 33  |..^.f.^.f.....f3|
00000170  d2 66 f7 f1 66 a3 66 02  66 a1 42 02 66 03 06 5e  |.f..f.f.f.B.f..^|
00000180  02 66 a3 46 02 66 83 3e  32 02 00 0f 84 1d 00 66  |.f.F.f.>2......f|
00000190  83 3e 36 02 00 0f 84 c8  fd 66 8b 1e 36 02 1e 07  |.>6......f..6...|
000001a0  66 8b 3e 46 02 66 a1 2a  02 e8 bc 01 66 0f b7 0e  |f.>F.f.*....f...|
000001b0  00 02 66 b8 02 02 00 00  e8 fe 07 66 0b c0 00 02  |..f........f....|
000001c0  02 01 07 fe ff ff 3f 00  00 00 81 35 e0 e8 00 00  |......?....5....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-07-26
Grub defaults to install to sda as that is the most common drive and is usually correct. But in multi-drive cases you should use manual install and choose which drive to install grub to.

It looks like you are booting from sdf in BIOS.

But the grub in sda is looking for a partition that does not exist (see UUID), so even if you set sda as boot drive it will not boot. You will just get grub rescue or grub prompt.

If you want to boot from sdf you just need to reinstall grub2's boot loader to sdf.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5  to sdf5 and sda to sdf or whatever dirve it comes up as from liveCD:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Grub also stores a location to reinstall to, so after booting run this also:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by LooneyLoonz on 2011-07-26
Ok great! so I basically reinstalled mint and made sure that I installed the boot loader to /dev/sdf, once installation was done, I rebooted and LO and BEHOLD! It now takes me to the grub boot loader! YAY!

...... Or so I thought.....

I now chose the option to boot Linux Mint and after a while, I am presented with a command line that starts off with:

BusyBox v1.17


(initramfs)

wtf???? why is it not booting into linux mint???

how do I solve this now?

---

### Post by oldfred on 2011-07-26
I would first try reinstaling grub2's boot loader as posted in the links  above.

---

### Post by LooneyLoonz on 2011-07-27
So after tinkering around a bit, I managed to boot into mint. What I did was:

getting to grub menu, pressing e on the mint boot /dev/sdf4

typing kernal commands acpi=off and pci=bios and then loading the mint boot which seemed to actually boot.

I am not even sure what that means, but it did allow me to boot. However, this whole installation seems buggered. Everything seems slow, a lot slower than my windows 7 installation. So there is something definately wrong, still.

I'm not sure if I should just do yet another clean install. What if I land up getting to the exact same place that I am now. I would have wasted all this time.

It just doesn't make sense. This thing should work out the box.

---

### Post by oldfred on 2011-07-27
I do not know about Mint.

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by BrokenKingpin on 2011-07-27
Did you install from a USB key? I have had issues where grub get installed to the USB key instead of the hard drive the OS was installed to. If this is the case you should be able to boot back into the live installer and recover the grub install.

---

### Post by LooneyLoonz on 2011-07-27
I have figure out what the problem is. My ssd drive was set to ahci mode, which is what its meant to be especially for windows. For some reason linux doesn't like that. I by chance decided to try switch to IDE mode and try it. After setting back to IDE mode, everything is working now. Grub appears and now I am able to boot into mint.

The problem: I dont want to use IDE mode. I want to use AHCI mode, considering thats what i use for windows 7.

Does anyone know how to solve this problem?

---

