---
title: "Windows 7 is not installing?"
date: 2011-09-19
forum: Any Other OS
---

### Post by sakibmoon on 2011-09-19
A few months ago, I installed Windows 7 on F: partition formatting my C: drive( The earlier windows 7 was on this partition). Later I installed Windows XP on G: drive. I didn't get windows 7 on boot menu. Later I used VistaBootpro to go back to Windows 7, but I couldn't fix the boot menu so that both of the OS appear in the boot menu. I had to select the boot menu to select which one I want to use to enter on next reboot. I think the boot menu was on C: drive as in the boot menu I got another option to boot from C: drive which returned a error.

Later I decide to try Ubuntu 10.04 and installed it in C: drive. I wanted to make dualboot windows 7 and ubuntu. I tried to recover windows 7 using bootable USB. Under recovery mode, it could find Windows installation on F: drive, but couldn't add it to boot menu. So, I decided to reinstall it. I formatted both of the F: and G: drive and then tried to install it. But Windows couldn't install it on F: or G: drive. I was surprised and quit the installation. When I rebooted I could no longer go to ubuntu. I was stuck on Grub rescue prompt. I found how to recover grub tutorial and followed it, but it returned error on every partition saying "unknown file system". ( It was supposed to find grub on linux partition, but it didn't happen ). Now I have installed Ubuntu 10.10 on deleting former Ubuntu partition. 

I need Windows 7 for some tasks. I am afraid that if I try to install it again, it might corrupt grub again. What should I do? Should I try installing it in a partition next to Ubuntu which is D: drive?

---

### Post by sakibmoon on 2011-09-19
I think my post has become very large and it is tiring to read all of it. So here is the simple version of what I want to do.

I had Ubuntu 10.04 on my system which was previously C: drive. I tried to install Windows 7 on F: partition and formatted it. Windows 7 installation failed for some reason and grub was corrupted. Grub recovery failed and I had to reinstall Ubuntu again. Now I want to install Windows 7. Why Windows couldn't install it on F: drive and what should I do to reinstall it.

---

### Post by Elfy on 2011-09-19
Thread moved to Other OS/Distro Talk.

---

### Post by sakibmoon on 2011-09-19
Thanks forestpiskie. I was unsure where to post this thread as I didn't notice this category. Sorry for troubling you.

---

### Post by sffvba[e0rt on 2011-09-20
I have never installed Windows after Linux... it is possible but the easiest way is to start with Windows... install it and then after that get Linux installed...

As for issues getting Windows installed on your F drive, not sure... as long as Windows installed itself there successfully it would have marked that partition as the boot partition and it should be able to boot from it...


404

---

### Post by coffeecat on 2011-09-20
> **not found said:**
> it is possible but the easiest way is to start with Windows... install it and then after that get Linux installed...

+1

@sakibmoon, there are two issues to consider (that I know of) when installing Windows after Linux. The first you mentioned - overwriting grub. It doesn't actually corrupt grub, as you put it. It overwrites the 440 bytes of grub code in the mbr and replaces it with Windows booting code. That's fairly easily fixed with an Ubuntu live CD. The more serious problem is if you have logical partitions on your hard drive and less than the full complement of primary partitions. The Windows installer can then do some strange things to the partition table. Or, at least, XP and Vista did in the simulations I ran. I haven't tried Windows 7 yet, but it would be best to be cautious.

But to your specific problem. D:, F: and G: drives and so on are a Windows convention and don't really mean much. In particular, they do not distinguish between primary and logical partitions, which is important when dealing with Windows. Windows must have its boot files on a primary partition. So that we can see what your current partition layout is like and advise appropriately, boot into an Ubuntu live CD, choose "try Ubuntu", connect to the internet from the live session and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there and post the contents of your RESULTS.txt between [noparse]```
 and 
```[/noparse] tags for readability. We can take it from there.

---

### Post by sakibmoon on 2011-09-20
> **not found said:**
> I have never installed Windows after Linux... it is possible but the easiest way is to start with Windows... install it and then after that get Linux installed...

As for issues getting Windows installed on your F drive, not sure... as long as Windows installed itself there successfully it would have marked that partition as the boot partition and it should be able to boot from it...


404

At the beginning, I installed Windows and then Ubuntu. I tried to recover Windows but it was a failure. MBR couldn't attach it to its boot menu for some reason. I think F: drive was not primary and the boot menu was on C: drive, so probably the boot files were on C: on which I installed Ubuntu.

[QUOTE=coffeecat]The first you mentioned - overwriting grub. It doesn't actually corrupt  grub, as you put it. It overwrites the 440 bytes of grub code in the mbr  and replaces it with Windows booting code. That's fairly easily fixed  with an Ubuntu live CD.[/QUOTE]If MBR overwrites grub, shouldn't I go to windows boot menu when PC starts. But in my case, it was grub rescue prompt and grub couldn't find any filesystem. Later when I installed Ubuntu again, I saw that Ubuntu file system was formatted. I didn't format it, maybe Windows did it automatically.(It's pretty weird.)

I think the problem is I tried to install Windows on Extended partition. Now, what are my options. I don't want to start fresh start again. How can I make a drive primary from extended?

Now, my system partition starts with Swap and then Linux file system which are primary. The later are extended partition.( See attached image )

---

### Post by coffeecat on 2011-09-20
From your posted Disk Utility screenshot I can see that none of your NTFS partitions are primary, and they all look to be data partitions. You really need to run the bootscript. There is a mass of useful information in that which Disk Utility does not show.

By the way, Disk Utility is showing a few bad sectors. You would be advised to look at the SMART data and run the self-tests.

---

### Post by sakibmoon on 2011-09-20
I can't run bootscript now as I don't have Live CD now. I have to make bootable USB and I will run them tomorrow or day after tomorrow. I will post the results after I run bootscript.

I have run self-test and it says that there are 2 bad sectors. Is it possible to recover them?

---

### Post by coffeecat on 2011-09-20
If the other parameters are not giving you any warnings, 2 bad sectors may not be anything to worry about. You can't recover them. The drive firmware on modern drives monitors the drive and remaps sectors when they go bad. If you are not getting a SMART warning at this stage, simply checking the bad sector count to make sure it is not rising will probably suffice at this stage. More here on bad sectors:

[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector) 

I have the thread subscribed, so I'll see your bootscript output when you post it.

---

### Post by sffvba[e0rt on 2011-09-20
> **sakibmoon said:**
> I can't run bootscript now as I don't have Live CD now. I have to make bootable USB and I will run them tomorrow or day after tomorrow. I will post the results after I run bootscript.

I have run self-test and it says that there are 2 bad sectors. Is it possible to recover them?

The default for most scan utilities are to mark them bad to prevent the sectors from being used... depending on what you used to scan there may be options to recover...

Also, failing sectors typically points to impending hardware failure so I [s]wouldn't[/s] **would** make sure I have backups of any critical data.


404

*edit: lol, edit the top... backups are important :p (thx coffeecat)*

---

### Post by sakibmoon on 2011-09-24
I have run boot_info_script.sh and the results are following:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.........$....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1434528 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     40,965,811   488,374,271   447,408,461   f W95 Extended (LBA)
/dev/sda5          40,965,813   143,364,059   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda6         143,364,123   266,229,179   122,865,057   7 NTFS / exFAT / HPFS
/dev/sda7         266,229,243   389,094,299   122,865,057   7 NTFS / exFAT / HPFS
/dev/sda8         389,097,472   488,374,271    99,276,800   7 NTFS / exFAT / HPFS
/dev/sda2               2,048     2,000,895     1,998,848  82 Linux swap / Solaris
/dev/sda3           2,000,896    40,964,095    38,963,200  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       417d740a-7ac4-4af9-8437-2058dd9cc8df   ext3       
/dev/sda2        068a41af-3cf1-41f5-8ba6-3673ae80123d   swap       
/dev/sda3        e017b16a-c75c-478e-963d-193688304ac7   ext4       
/dev/sda5        8248A5B648A5A97D                       ntfs       SOFT & SONGS
/dev/sda6        B25EAA5B5EAA185D                       ntfs       GAMES
/dev/sda7        3A68DC2168DBD9A9                       ntfs       MOVIE
/dev/sda8        4688B4CC333DCEF6                       ntfs       Soft and Others
/dev/sdb1        D8DC-D3E8                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
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

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=e017b16a-c75c-478e-963d-193688304ac7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=e017b16a-c75c-478e-963d-193688304ac7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e017b16a-c75c-478e-963d-193688304ac7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e017b16a-c75c-478e-963d-193688304ac7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set e017b16a-c75c-478e-963d-193688304ac7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e017b16a-c75c-478e-963d-193688304ac7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=068a41af-3cf1-41f5-8ba6-3673ae80123d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  17.148494720 = 18.413056000   boot/grub/core.img                             1
  17.132450104 = 18.395828224   boot/grub/grub.cfg                             2
   1.968948364 = 2.114142208    boot/initrd.img-2.6.35-22-generic              2
   1.983921051 = 2.130219008    boot/initrd.img-2.6.35-30-generic              2
  17.208099365 = 18.477056000   boot/vmlinuz-2.6.35-22-generic                 1
  17.216178894 = 18.485731328   boot/vmlinuz-2.6.35-30-generic                 1
   1.983921051 = 2.130219008    initrd.img                                     2
   1.983921051 = 2.130219008    initrd.img.old                                 2
  17.216178894 = 18.485731328   vmlinuz                                        1
  17.216178894 = 18.485731328   vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by sakibmoon on 2011-09-24
What are my options now? How can I install Windows now?

It would be great if you can explain how can you decide what to do from these texts.

---

### Post by coffeecat on 2011-09-24
**EDIT**: wait a moment. I misread your boot script output. The primaries are at the beginning of the drive. Apologies. I will post again in a moment.

Your boot script output is showing something that was only half-shown by Disk Utility. Your partition layout is a big obstacle to installing Windows. What you have is an extended partition (sda1) [s]starting at the beginning of the drive[/s] which contains four NTFS logical partitions (sda5 to sda8 ) which are labelled "SOFT & SONGS", "GAMES", "MOVIE" and "Soft and Others". I'll leave you to match them with your former Windows D:, E:, F: and so on drive letters. At the [s]end[/s] beginning of the drive are two primary partitions, sda2 and sda3, which are your swap and Ubuntu root partitions respectively.

[s]An extended partition at the beginning is unusual but shouldn't prevent Windows from installing to a primary at the end, but[/s] your primaries are Linux partitions. You cannot install Windows to one of the four NTFS partitions, because they are logical partitions, that is unless you had a spare primary partition for the Windows boot files, which you don't.  Stalemate. I cannot see a way of (easily) re-arranging your partitions so that you can install Windows. It is theoretically possible by shrinking one or more of the NTFS partitions and shrinking the extended partition to make room [s]at the beginning[/s] for a primary partition for Windows, but that would take a very long time indeed and would risk data corruption if something went wrong with any of the partition manipulations you will have to do.

What would I do if this was my system? I would backup all my personal files onto other media, completely wipe the whole drive and start again. I would start by creating a single partition for Windows and install Windows to it. Then I would create my data partitions and Linux partitions and re-install Ubuntu. It would be quicker.

See what others think and, in the meantime, I'll have a closer look at your bootscript output to see if there is anything else to comment on.

---

### Post by coffeecat on 2011-09-24
OK, I won't remove the misinformation from my previous post- I'll do a strikethrough. We all make mistakes! :)

The way the partitions were listed in your boot script output threw me at first, but the start and end sector numbers show the real situation. Your partition order on the drive is:

sda2
sda3
sda1 (extended)
With logicals:
sda5
sda6
sda7
sda8

Which is still confusing.

Your sda2 is the swap which is approx 1GB. sda3 is your Ubuntu root partition which is approx 20GB. But then comes your extended partition. Same story really. You would need to resize the extended and some of the logicals to create room for a primary partition for Windows. In my opinion, it would be better to start over with a new partition layout with Windows on the first partition which has to be primary. Always easier that way.

---

### Post by sakibmoon on 2011-09-24
That means, I have to format current Ubuntu installation and install Windows on it. If I try to install Ubuntu on a partition next to Windows installation, will I face any difficulty (Like the one I faced when tried to install windows)? If this is the easiest way, I will do that.

I also want to look for other option if possible. Is it possible to make a portion of the extended partition primary? I know if it was easy, you would recommend that, I just want to know if it is possible.

And yes, thanks a lot for your quick response. I didn't expect that I would get response this quick.

---

### Post by coffeecat on 2011-09-24
> **sakibmoon said:**
> Is it possible to make a portion of the extended partition primary?

No. That is impossible. An extended partition is simply a special type of primary partition whose sole purpose is to contain logical partitions. This is to get round the limitation of the mbr partition scheme which allows a maximum of four primary partitions. You cannot have a primary partition within an extended partition. 

Rather than answer your other questions, it's better if I link you to the Ubuntu documentation how to partition guide:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Read through all the links. It will give you a good idea of the essentials of partitioning, and you will have a better understanding of what is and what is not possible.

Someone else may see a way that I haven't to achieve what you want, but it's still worth your while reading that guide.

---

### Post by sakibmoon on 2011-09-24
I found my answer about my previous post. So, here is my plan. Let me know if I could face any problem or anything is wrong in the process.

-> I will shrink the swap and Ubuntu partition and install Windows on it.
-> When installing Windows I will make two partition next to primary partition, which is currently 53 GB( 25 GB each or 20+30 GB ).
-> I will install Ubuntu on the next to primary partition.

Is anything wrong in above steps? 
If not, what is the best thing to do to recover Windows on the boot menu. I have seen a few articles about it, but I want your suggestion about it.

---

### Post by coffeecat on 2011-09-25
> **sakibmoon said:**
> 
-> I will shrink the swap and Ubuntu partition and install Windows on it.

You won't have enough room. The swap and Ubuntu partitions together are only about 21GB. 

> **sakibmoon said:**
> 
-> When installing Windows I will make two partition next to primary partition, which is currently 53 GB( 25 GB each or 20+30 GB ).
-> I will install Ubuntu on the next to primary partition.

No. Your large partitions are logical ones, not primary ones. That is the fundamental problem. You could shrink the "SOFT & SONGS" partition and then shrink the extended partition by moving the start boundary to the right, and then you could create a primary partition in the freed space, but only after shrinking the extended partition. It would probably work, but will give you virtually no flexibility for the future. That is why I suggested a complete new layout - sorry if I didn't make that clear.

As a general principle it is much easier to leave the beginning area of the drive for Windows. Windows needs a primary partition to boot from and it is so much tidier and easier to work with if the Windows C: partition comes before any others. Linux can boot from logical partitions, and it's a good plan to keep Linux in logical partitions so that you have flexibilty within the 4-primary partition limitation of the mbr partition table. At the moment, two of your primaries are used up with Linux partitions, which is unnecessary. That was another reason for my saying that if this was my system, I would completely re-organise the partition layout.

Another point: you have four NTFS data partitions which is an inefficient use of space. Why not have one single large data partition with "SOFT & SONGS", "GAMES", "MOVIE" and "Soft and Others" folders within it? Or however you would like to re-arrange how you organise your personal files. If you did that, you could have a partition layout something like this:

sda1 - primary - Windows C:
sda2 - primary - NTFS - for sharing all data files between Windows and Ubuntu.
Partition 3 - extended partition containing all your Ubuntu logical partitions.

Something to think about.

---

### Post by sakibmoon on 2011-09-25
> **coffeecat said:**
> 
Another point: you have four NTFS data partitions which is an inefficient use of space. Why not have one single large data partition with "SOFT & SONGS", "GAMES", "MOVIE" and "Soft and Others" folders within it? Or however you would like to re-arrange how you organise your personal files. If you did that, you could have a partition layout something like this:

sda1 - primary - Windows C:
sda2 - primary - NTFS - for sharing all data files between Windows and Ubuntu.
Partition 3 - extended partition containing all your Ubuntu logical partitions.

Something to think about.

I have decided to reorganize the partition layout as you have suggested. I am currently backing up my data on external device. So, what should I use to reorganize the partition table? Should I boot from a Live Ubuntu CD to create new partition table using Gparted and then try to install Windows.

---

### Post by coffeecat on 2011-09-25
You don't necessarily need to create a new partition table - simply delete all the partitions using Gparted in the live CD. However, creating a new partition table is a quick and easy way of clearing all the partitions in one go so, yes, that is what I would do. When you first open Gparted, you'll find that the live session has mounted the swap partition and there will be a lock icon by it. Right-click on it and choose "swapoff" otherwise you won't be able to delete it or create a new partition table.

Left to itself, the Windows 7 installer prefers to create two partitions for Windows: a 100-200MB "SYSTEM" partition which contains the boot files, and the larger C: partition. If you create a single NTFS partition in Gparted before starting the Windows installer, you can tell it to install everything to that one partition. Whichever you use to create the Windows partition, the Windows installer or Gparted, only create the NTFS partition(s) for Windows itself at first. Don't create a NTFS data partition yet - leave the rest of the drive unallocated for now. Once you've installed Windows and you've confirmed that it's working, then is the time to boot the live Ubuntu CD, make the rest of your partitions and install Ubuntu.

There are those who will say you should use Windows to create NTFS partitions both for the "C:" drive and for a data partition. All I can say is that I have installed XP, Vista and Windows 7 to NTFS partitions created by Gparted and they have run satisfactorily, and have been able to use NTFS data partitions also created with Gparted.

---

### Post by sakibmoon on 2011-09-26
> **coffeecat said:**
> You don't necessarily need to create a new partition table - simply delete all the partitions using Gparted in the live CD. However, creating a new partition table is a quick and easy way of clearing all the partitions in one go so, yes, that is what I would do. When you first open Gparted, you'll find that the live session has mounted the swap partition and there will be a lock icon by it. Right-click on it and choose "swapoff" otherwise you won't be able to delete it or create a new partition table.
 
Left to itself, the Windows 7 installer prefers to create two partitions for Windows: a 100-200MB "SYSTEM" partition which contains the boot files, and the larger C: partition. If you create a single NTFS partition in Gparted before starting the Windows installer, you can tell it to install everything to that one partition. Whichever you use to create the Windows partition, the Windows installer or Gparted, only create the NTFS partition(s) for Windows itself at first. Don't create a NTFS data partition yet - leave the rest of the drive unallocated for now. Once you've installed Windows and you've confirmed that it's working, then is the time to boot the live Ubuntu CD, make the rest of your partitions and install Ubuntu.
 
There are those who will say you should use Windows to create NTFS partitions both for the "C:" drive and for a data partition. All I can say is that I have installed XP, Vista and Windows 7 to NTFS partitions created by Gparted and they have run satisfactorily, and have been able to use NTFS data partitions also created with Gparted.
 
+1
 
I followed your suggestion and everything has worked great. So, here is what I've done:
 
-> At first, I booted from Ubuntu Live CD and then Created new partition table using Gparted. I didn't create any partition, just merged all the existing partition.
 
-> Then I installed Windows 7 Professional. I only created 30 GB NTFS partition to install Windows. I left the remaining space unallocated.
 
-> After that, I installed Ubuntu. I created a swap partition and a 20 GB Ext4 partition to install Ubuntu. There was no option to make a partition NTFS, so I choose the option "do not use this partition" for the remaining 196 GB. I created this as a Primary partition.
 
-> After installing Ubuntu 10.10, I installed Gparted and formatted the data portion as NTFS.
 
So, now I have dualboot Windows and Ubuntu and everything is working great. I am posting this from Windows OS.
 
Thanks a lot to [COLOR=#ff0000]**coffeecat**[/COLOR][COLOR=black] for his continuous support. So, my partition table looks like this now:[/COLOR]
 
/dev/sda1 --- System reserved (NTFS)
/dev/sda2 --- Windows 7 (NTFS)
/dev/sda3 --- Data portion (NTFS)
/dev/sda5 --- Ubuntu 10.10 (Ext4)
/dev/sda6 --- Swap area
(See the attached image)

---

### Post by coffeecat on 2011-09-26
Yes, that looks to be a nice tidy setup. I'm puzzled as to why Gparted in the live CD wouldn't format your sda3 as NTFS. Gparted needs the ntfsprogs package to be able to create NTFS filesystems and ntfsprogs *should* be on the live CD. A mystery. But never mind - you found a solution.

Good luck!

---

