---
title: "Installed BT5R3, Grub Rescue No Such Device on boot"
date: 2012-08-25
forum: Any Other OS
---

### Post by lalaithan on 2012-08-25
I installed Backtrack 5 R3 (single boot) today and upon restart (booting from hard disk) I get the grub rescue no such device. I booted from the liveCD and got this in the terminal when I went to re-install grub:
 ```
root@bt:~# sudo bash
root@bt:~# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026fec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38166   306563072   83  Linux
/dev/sda2           38166       38914     6005761    5  Extended
/dev/sda5           38166       38914     6005760   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15506   117218304    7  HPFS/NTFS
root@bt:~# mount /dev/sda1/mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab

```  Any ideas on how to fix this issue? I'm at a loss.

---

### Post by coffeecat on 2012-08-26
> **lalaithan said:**
> 
 ```
root@bt:~# mount /dev/sda1/mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab

```

If you are trying to mount /dev/sda1 to the /mnt directory in order to re-install grub, you made a typo with the mount command. There should be a space between "/dev/sda1" and "/mnt", thus:

```
mount /dev/sda1 /mnt
```

---

### Post by lalaithan on 2012-08-26
I reinstalled Grub 2 and I am still getting the "error : no such device: " with some numbers and letters after. Is there a way to fix this?

---

### Post by coffeecat on 2012-08-26
That probably means that grub is installed to the mbr, but is pointing to the wrong partition. What command did you use to re-install grub?

---

### Post by lalaithan on 2012-08-26
> **coffeecat said:**
> That probably means that grub is installed to the mbr, but is pointing to the wrong partition. What command did you use to re-install grub?

I followed the instructions at [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by coffeecat on 2012-08-26
> **lalaithan said:**
> I followed the instructions at [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

That thread describes as least two ways for re-installing grub, which doesn't answer the question. Which exact commands did you run? We need to see what might have gone wrong or whether you substituted the wrong values in sdXY for example.

---

### Post by lalaithan on 2012-08-26
> **coffeecat said:**
> That thread describes as least two ways for re-installing grub, which doesn't answer the question. Which exact commands did you run? We need to see what might have gone wrong or whether you substituted the wrong values in sdXY for example.
I followed from LiveCD, option C, with an internet connection. I don't know exactly what I typed in because I've restarted the computer and didn't save the commands.

---

### Post by coffeecat on 2012-08-26
Try this from the live CD with the "root@bt:~#" terminal prompt:

```
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt /dev/sda
```

---

### Post by lalaithan on 2012-08-26
> **coffeecat said:**
> Try this from the live CD with the "root@bt:~#" terminal prompt:

```
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt /dev/sda
```

It installs, but I get the same message when I try to boot from hard drive.

---

### Post by coffeecat on 2012-08-26
> **lalaithan said:**
> It installs, but I get the same message when I try to boot from hard drive.

Since sda1 is your only Linux partition, I can only assume that something is wrong with the BT installation itself. It may or may not provide any further useful information, but it would be advisable to see what the boot info script tells us. Boot up the live BT CD, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by lalaithan on 2012-08-27
Here's the results:  ```
     Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 9fde6028-8821-49ee-bb8c-c6a3d4e81e08 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 507795512 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 256 for /boot/grub.
    Operating System:  BackTrack 5 R3 - 64 Bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   613,128,191   613,126,144  83 Linux
/dev/sda2         613,130,238   625,141,759    12,011,522   5 Extended
/dev/sda5         613,130,240   625,141,759    12,011,520  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   234,438,655   234,436,608   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        910186ea-1386-4f15-9029-179e985de02d   ext4       
/dev/sda5        dd4f7dae-5346-4f55-8465-721e43039ad1   swap       
/dev/sdb1        009F9CEE04479220                       ntfs       
/dev/sr0                                                iso9660    BT5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
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
search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 3.2.6' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
    linux    /boot/vmlinuz-3.2.6 root=UUID=910186ea-1386-4f15-9029-179e985de02d ro   quiet splash
    initrd    /boot/initrd.img-3.2.6
}
menuentry 'Ubuntu, with Linux 3.2.6 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
    echo    'Loading Linux 3.2.6 ...'
    linux    /boot/vmlinuz-3.2.6 root=UUID=910186ea-1386-4f15-9029-179e985de02d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.6
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 242.133419037 = 259.988779008  boot/grub/core.img                             1
 170.148002625 = 182.695026688  boot/grub/grub.cfg                             1
   0.180664062 = 0.193986560    boot/initrdf.img-3.2.6                         2
   2.469726562 = 2.651848704    boot/initrd.img-3.2.6                          3
   0.196289062 = 0.210763776    boot/initrds.img-3.2.6                         2
 242.132995605 = 259.988324352  boot/vmlinuz-3.2.6                             1
   2.469726562 = 2.651848704    initrd.img                                     3
 242.132995605 = 259.988324352  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f3 a4 1f 10 cf 7f 00 00  10 04 00 00 02 00 00 00  |................|
00000010  00 00 00 00 00 00 00 00  08 00 00 00 08 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  f3 a4 1f 10 cf 7f 00 00  20 04 00 00 02 00 00 00  |........ .......|
00000050  00 00 00 00 00 00 00 00  08 00 02 00 08 00 02 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  f3 a4 1f 10 cf 7f 00 00  30 04 00 00 02 00 00 00  |........0.......|
00000090  00 00 00 00 00 00 00 00  08 00 03 00 08 00 03 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000c0  f3 a4 1f 10 cf 7f 00 00  40 04 00 00 02 00 00 00  |........@.......|
000000d0  00 00 00 00 00 00 00 00  08 00 04 00 08 00 04 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  f7 a4 1f 10 cf 7f 00 00  10 05 00 00 02 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  08 00 00 00 08 00 00 00  |................|
00000120  08 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  f7 a4 1f 10 cf 7f 00 00  20 05 00 00 02 00 00 00  |........ .......|
00000150  00 00 00 00 00 00 00 00  08 00 02 00 08 00 02 00  |................|
00000160  08 00 02 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  f7 a4 1f 10 cf 7f 00 00  30 05 00 00 02 00 00 00  |........0.......|
00000190  00 00 00 00 00 00 00 00  08 00 03 00 08 00 03 00  |................|
000001a0  08 00 03 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 48 b7 00 00 00  |...........H....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

ile descriptor 15 (socket:[30899]) leaked on lvscan invocation. Parent PID 7399: /bin/bash
```

---

### Post by coffeecat on 2012-08-27
The boot script output shows grub correctly installed to the mbr and looking to the correct partition. Everything else seems OK, except that you also have grub installed to the boot sector of /dev/sda1 - it shouldn't be there. My guess is that you overrode the default /dev/sda for the installation of grub when you ran the Backtrack installer, or that you mistakenly installed grub to sda1 instead of sda on one of the occasions when you re-installed grub from the live CD.

I'm not sure that is the problem, though. Although grub shouldn't be in the partition boot sector in your setup, I don't believe it would interfere with booting, so I'm puzzled at the moment. I'll contact someone else and get them to have a look at this thread as well.

**EDIT**: with a second look, this bit concerns me:

```
sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 507795512 of the same hard 
                       drive for core.img. [COLOR="Red"]core.img is at this location and 
                       looks in partition 256 for /boot/grub[/COLOR].
    Operating System:  BackTrack 5 R3 - 64 Bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

That could be the problem after all. Let's wait until we get the second opinion - I've pm'd them.

---

### Post by lalaithan on 2012-08-28
I went ahead and ran boot repair and it didn't fix the no such device error. I am confused by the appearance of the Windows Vista/7 partition, it shouldn't still be there? Also, the numbers/letters after "no such device" match```
 /dev/sda1        **910186ea-1386-4f15-9029-179e985de02d**   ext4
```. Could this be that the hard drive is actually the issue? These aren't exactly "spring chickens" in hard drive age.

```
  Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 507795512 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 256 for /boot/grub.
    Operating System:  BackTrack 5 R3 - 64 Bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   613,128,191   613,126,144  83 Linux
/dev/sda2         613,130,238   625,141,759    12,011,522   5 Extended
/dev/sda5         613,130,240   625,141,759    12,011,520  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   234,438,655   234,436,608   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        910186ea-1386-4f15-9029-179e985de02d   ext4       
/dev/sda5        dd4f7dae-5346-4f55-8465-721e43039ad1   swap       
/dev/sdb1        009F9CEE04479220                       ntfs       
/dev/sr0                                                iso9660    BT5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
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
search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 3.2.6' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
	linux	/boot/vmlinuz-3.2.6 root=UUID=910186ea-1386-4f15-9029-179e985de02d ro   quiet splash
	initrd	/boot/initrd.img-3.2.6
}
menuentry 'Ubuntu, with Linux 3.2.6 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
	echo	'Loading Linux 3.2.6 ...'
	linux	/boot/vmlinuz-3.2.6 root=UUID=910186ea-1386-4f15-9029-179e985de02d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.6
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 910186ea-1386-4f15-9029-179e985de02d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 242.133419037 = 259.988779008  boot/grub/core.img                             1
 242.136047363 = 259.991601152  boot/grub/grub.cfg                             1
   2.469726562 = 2.651848704    boot/initrd.img-3.2.6                          3
   0.180664062 = 0.193986560    boot/initrdf.img-3.2.6                         2
   0.196289062 = 0.210763776    boot/initrds.img-3.2.6                         2
 242.132995605 = 259.988324352  boot/vmlinuz-3.2.6                             1
   2.469726562 = 2.651848704    initrd.img                                     3
 242.132995605 = 259.988324352  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f3 a4 1f 10 cf 7f 00 00  10 04 00 00 02 00 00 00  |................|
00000010  00 00 00 00 00 00 00 00  08 00 00 00 08 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  f3 a4 1f 10 cf 7f 00 00  20 04 00 00 02 00 00 00  |........ .......|
00000050  00 00 00 00 00 00 00 00  08 00 02 00 08 00 02 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  f3 a4 1f 10 cf 7f 00 00  30 04 00 00 02 00 00 00  |........0.......|
00000090  00 00 00 00 00 00 00 00  08 00 03 00 08 00 03 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000c0  f3 a4 1f 10 cf 7f 00 00  40 04 00 00 02 00 00 00  |........@.......|
000000d0  00 00 00 00 00 00 00 00  08 00 04 00 08 00 04 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  f7 a4 1f 10 cf 7f 00 00  10 05 00 00 02 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  08 00 00 00 08 00 00 00  |................|
00000120  08 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  f7 a4 1f 10 cf 7f 00 00  20 05 00 00 02 00 00 00  |........ .......|
00000150  00 00 00 00 00 00 00 00  08 00 02 00 08 00 02 00  |................|
00000160  08 00 02 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  f7 a4 1f 10 cf 7f 00 00  30 05 00 00 02 00 00 00  |........0.......|
00000190  00 00 00 00 00 00 00 00  08 00 03 00 08 00 03 00  |................|
000001a0  08 00 03 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 48 b7 00 00 00  |...........H....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (pipe:[22551]) leaked on lvscan invocation. Parent PID 18563: bash
File descriptor 10 (pipe:[22551]) leaked on lvscan invocation. Parent PID 18563: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-28__15h31 ===================
boot-repair version : 3.18-0ppa50~lucid
boot-sav version : 3.192-0ppa17~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
boot-repair is executed in live-session (Ubuntu 10.04.3 LTS, lucid, Ubuntu, x86_64)
CPU op-mode(s):        64-bit
sudo: cannot get working directory

=================== os-prober:
/dev/sda1:Ubuntu 10.04.3 LTS (10.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="BT5" TYPE="iso9660"
/dev/sda1: UUID="910186ea-1386-4f15-9029-179e985de02d" TYPE="ext4"
/dev/sda5: UUID="dd4f7dae-5346-4f55-8465-721e43039ad1" TYPE="swap"
/dev/sdb1: UUID="009F9CEE04479220" TYPE="ntfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 2012-08-26 10:55 grub.d
total 40
-rwxr-xr-x 1 root root 4444 2011-04-27 06:28 00_header
-rwxr-xr-x 1 root root 1416 2011-04-27 06:06 05_debian_theme
-rwxr-xr-x 1 root root 4843 2011-04-27 06:28 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 05:40 20_memtest86+
-rwxr-xr-x 1 root root 6605 2011-04-27 06:28 30_os-prober
-rwxr-xr-x 1 root root  214 2011-04-27 06:28 40_custom
-rw-r--r-- 1 root root  483 2011-04-27 06:28 README




=================== dmesg | grep EFI :
This live-session is not EFI-compatible.
[    1.429868] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  314GB  314GB   primary   ext4            boot
2      314GB   320GB  6150MB  extended
5      314GB   320GB  6150MB  logical   linux-swap(v1)


Model: ATA ST3120025A (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  120GB  120GB  primary  ntfs         boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.

                                                                          
Error: /dev/fd0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd fd0 fd0u1040 fd0u1120 fd0u1440 fd0u1600 fd0u1680 fd0u1722 fd0u1743 fd0u1760 fd0u1840 fd0u1920 fd0u360 fd0u720 fd0u800 fd0u820 fd0u830 full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs   1002M  154M  848M  16% /
none      devtmpfs    991M  256K  991M   1% /dev
/dev/sr0   iso9660    3.2G  3.2G     0 100% /cdrom
/dev/loop0
squashfs    3.1G  3.1G     0 100% /rofs
none         tmpfs   1002M     0 1002M   0% /dev/shm
tmpfs        tmpfs   1002M   20K 1002M   1% /tmp
none         tmpfs   1002M   60K 1002M   1% /var/run
none         tmpfs   1002M     0 1002M   0% /var/lock
none         tmpfs   1002M     0 1002M   0% /lib/init/rw
/dev/sda1     ext4    293G   16G  263G   6% /mnt/boot-sav/sda1
/dev/sdb1  fuseblk    112G   68M  112G   1% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026fec

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38166   306563072   83  Linux
/dev/sda2           38166       38914     6005761    5  Extended
/dev/sda5           38166       38914     6005760   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02cc02cb

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15506   117218304    7  HPFS/NTFS



=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda1 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Custom-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
fsck from util-linux-ng 2.17.2
Refusing to operate on read-write mounted device /dev/sdb1.
Unhide GRUB boot menu in sda1/etc/default/grub
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 1 boot on
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory

                                                                          
Information: You may need to update /etc/fstab.

sudo: cannot get working directory
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by YannBuntu on 2012-08-29
Hello

Your Ubuntu partition ends far (>100GB) from the start of the disk.

If i were you, i would use Gparted from liveCD to **reduce the sda1 partition to 100GB** (reduce it from its right-side so that it still starts at the start of the disk). You can create a data partition in the empty space.

Alternatively, you can create a little /boot partition at the start of the disk: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by lalaithan on 2012-08-30
> **YannBuntu said:**
> Hello

Your Ubuntu partition ends far (>100GB) from the start of the disk.

If i were you, i would use Gparted from liveCD to **reduce the sda1 partition to 100GB** (reduce it from its right-side so that it still starts at the start of the disk). You can create a data partition in the empty space.

That worked. Thanks for your assistance, YannBuntu and coffeecat!

---

### Post by YannBuntu on 2012-08-30
Good job! :guitar:
For my information (and for helping solving [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887")), is it the first time you install a Linux distribution on this particular computer? if no, which other distributions had you installed (name, version) ?

---

### Post by lalaithan on 2012-09-01
> **YannBuntu said:**
> Good job! :guitar:
For my information (and for helping solving [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887")), is it the first time you install a Linux distribution on this particular computer? if no, which other distributions had you installed (name, version) ?

It had Ubuntu 11.10 installed previously.

---

### Post by YannBuntu on 2012-09-03
> **lalaithan said:**
> It had Ubuntu 11.10 installed previously.

ok thanks.
What is the version of grub-common in BT5R3?  (if you don't know, please indicate the output of "grub-install -v")

---

