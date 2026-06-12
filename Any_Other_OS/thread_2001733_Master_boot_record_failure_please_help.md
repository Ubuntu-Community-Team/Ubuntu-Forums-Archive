---
title: "Master boot record failure please help"
date: 2012-06-11
forum: Any Other OS
---

### Post by NERDMAN! on 2012-06-11
I just tried to update my completely dead install of mint 12 by replacing it with mint 13. as testified by my presence on the Internet I was successful in making mint 13 work, the downside is I stuffed up pretty hard with the multi-booting.

the long and short of it is I have been using a multi-booted laptop with windows 7 and mint. I was stupid enough to forget grub could load windows and i went with the easyBCD method of chain-loading. (windows boot loader into grub installed on Linux partition)

so I was in windows using easyBCD to edit the master boot record and change the entry for Linux, and that's where I stuffed up. I thought I removed the old mint 12 (sda7) entry and replaced it with mint 13 (sda6), turns out I somehow removed windows entirely from the list, when I rebooted I had two options, mint 12 and mint 13, both of which led directly to mint 13.

unfortunately i require windows for both work and study purposes, and i now have a perfectly working windows partition i simply cant boot into.

thats my story, now I need some help. I need to know what my options are, can I install grub to the master boot record and have it load windows when I need it? can I access the windows bootloader list and manually edit it? or is my system a total writeoff and reformat?

---

### Post by wilee-nilee on 2012-06-11
From mint or a live cd run this command set, and post all the text from the results.txt that will show in home.

When you paste to a reply, with all of the text, highlight all of it, then click the # in the reply panel, then submit reply.
```

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by NERDMAN! on 2012-06-11
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

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
    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 613988520 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 1150660280 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive.
    Operating System:  Linux Mint 13 Maya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   584,480,767   584,069,120   7 NTFS / exFAT / HPFS
/dev/sda3         584,482,814 1,219,319,807   634,836,994   f W95 Extended (LBA)
/dev/sda5       1,158,512,640 1,219,319,807    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda6         584,482,816   592,480,255     7,997,440  82 Linux swap / Solaris
/dev/sda7         592,482,304 1,158,508,543   566,026,240  83 Linux
/dev/sda4       1,219,319,808 1,250,263,727    30,943,920  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CA5E2D995E2D7EF7                       ntfs       
/dev/sda2        9E682F2A682F009F                       ntfs       
/dev/sda4        88FE353CFE3523BA                       ntfs       LENOVO_PART
/dev/sda5        E49E715D9E7128E6                       ntfs       LENOVO
/dev/sda6        2dda1291-9236-48fd-9ec4-d3022ad54485   swap       
/dev/sda7        4ed01dee-0755-4a1a-ac59-38b038acedf1   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 4ed01dee-0755-4a1a-ac59-38b038acedf1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 4ed01dee-0755-4a1a-ac59-38b038acedf1
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
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
menuentry 'LinuxMint, with Linux 3.2.0-23-generic' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 4ed01dee-0755-4a1a-ac59-38b038acedf1
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4ed01dee-0755-4a1a-ac59-38b038acedf1 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'LinuxMint, with Linux 3.2.0-23-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 4ed01dee-0755-4a1a-ac59-38b038acedf1
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4ed01dee-0755-4a1a-ac59-38b038acedf1 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 4ed01dee-0755-4a1a-ac59-38b038acedf1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 4ed01dee-0755-4a1a-ac59-38b038acedf1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root CA5E2D995E2D7EF7
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 88FE353CFE3523BA
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
# / was on /dev/sda7 during installation
UUID=4ed01dee-0755-4a1a-ac59-38b038acedf1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2dda1291-9236-48fd-9ec4-d3022ad54485 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 548.677604675 = 589.138092032  boot/grub/core.img                             1
 396.665180206 = 425.915994112  boot/grub/grub.cfg                             1
 284.070705414 = 305.018597376  boot/initrd.img-3.2.0-23-generic               2
 300.651103973 = 322.821664768  boot/vmlinuz-3.2.0-23-generic                  1
 284.070705414 = 305.018597376  initrd.img                                     2
 300.651103973 = 322.821664768  vmlinuz                                        1


```

---

### Post by wilee-nilee on 2012-06-11
From the live cd we will chroot grub to the mbr run these commands.

```
sudo mount /dev/sda7 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```

Once in the mint install run.
```
sudo update-grub
```

---

### Post by oldfred on 2012-06-11
You have Windows in MBR and willee's instructions will get grub2's boot loader into the MBR if you do not want EasyBCD.

But you installed grub2's boot loader to the Windows PBR - partition boot sector. All NTFS partitions have to have partition info in them similar to partition table and if bootable which boot file to use bootmgr or ntldr.

If you only installed grub2's boot loader to the pbr once, you can use the backup to restore the correct PBR.

```
sda2: ______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
[COLOR=Red]    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 613988520 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by wilee-nilee on 2012-06-11
> **oldfred said:**
> You have Windows in MBR and willee's instructions will get grub2's boot loader into the MBR if you do not want EasyBCD.

But you installed grub2's boot loader to the Windows PBR - partition boot sector. All NTFS partitions have to have partition info in them similar to partition table and if bootable which boot file to use bootmgr or ntldr.

If you only installed grub2's boot loader to the pbr once, you can use the backup to restore the correct PBR.

```
sda2: ______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
[COLOR=Red]    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 613988520 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Oh shoot, DOH, good eye oldfred I missed that. ;)

---

### Post by NERDMAN! on 2012-06-11
thankyou for your help kind sir but that did not solve the issue, only extended it.
as per your instructions i now have grub on the master boot record, but when loading into windows 7 it goes right back to my stuffed windows bootloader, which is still configured for multibooting as stated in my first post. the issue is the windows bootloader menu does not contain a windows entry. only two linux entries. which puts me right back at square one again.

---

### Post by wilee-nilee on 2012-06-11
> **NERDMAN! said:**
> thankyou for your help kind sir but that did not solve the issue, only extended it.
as per your instructions i now have grub on the master boot record, but when loading into windows 7 it goes right back to my stuffed windows bootloader, which is still configured for multibooting as stated in my first post. the issue is the windows bootloader menu does not contain a windows entry. only two linux entries. which puts me right back at square one again.

Follow oldfreds post to clean out the grub you put in the windows partition.

I missed that part but what you have done so far is part of fixing this altogether.

If you want to go back to easybcd after you are all fixed you would just reload the MS bootloader to the mbr.

Honestly easybcd is not a good option, grub is much more flexible.

---

### Post by NERDMAN! on 2012-06-11
> **oldfred said:**
> You have Windows in MBR and willee's instructions will get grub2's boot loader into the MBR if you do not want EasyBCD.

But you installed grub2's boot loader to the Windows PBR - partition boot sector. All NTFS partitions have to have partition info in them similar to partition table and if bootable which boot file to use bootmgr or ntldr.

If you only installed grub2's boot loader to the pbr once, you can use the backup to restore the correct PBR.

```
sda2: ______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
[COLOR=Red]    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 613988520 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

i'm afraid i do not have the backup bootsector option as described in either of those guides.

i take it i'm going to need to hunt up my windows disk?

---

### Post by Perfect Storm on 2012-06-11
Moved to Other OS/Distro Talk.

---

### Post by oldfred on 2012-06-11
If the backup boot sector is also bad, you have to repair the boot sector. But Windows will not directly repair it as it does not see it as NTFS. 

So use testdisk to write a (basic) NTFS boot sector (rebuild BS). With XP that often worked, but with Windows 7 or Vista all it does is make it so you can then repair it with Windows repairCD or install CD in repair mode.

Then in Windows Repair console:

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Windows 7 has its own separate boot/repair partition which looks ok. So in your case can you boot into the repair from your sda1 partition. You may need to use f8 and from grub that is real quick or almost the same time as you hit enter in grub on the Windows entry. Otherwise you may have to move boot flag to sda2, as Windows normally only repairs the boot flagged partition. It probably will then make it fully bootable without the separate boot partition, so you may or may not want to move boot flag back to sda1. You can use gparted or Windows to move boot flag. In Windows it is makeactive.

---

### Post by NERDMAN! on 2012-06-12
wilee-nilee and oldfred, you guys will be remembered as living legends.

thanks for the help, rebuilt the bootsector, works like a charm.

thanks guys.

---

### Post by wilee-nilee on 2012-06-12
> **NERDMAN! said:**
> wilee-nilee and oldfred, you guys will be remembered as living legends.

thanks for the help, rebuilt the bootsector, works like a charm.

thanks guys.

Cool, sorry I missed that grub in the windows, it could of gone easier, thanks to oldfred it got done.

---

