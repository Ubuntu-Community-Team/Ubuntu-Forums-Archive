---
title: "Booting problems - partitions changed themselves?"
date: 2010-11-10
forum: Apple Hardware Users
---

### Post by _rex on 2010-11-10
So I recently acquired a friend's old Macbook, and immediately installed 10.04 as the sole operating system. After a day or two, a few restarts, and the system updates, it failed to boot with this message

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

and a Busybox.

I tried to read up on the subject [http://ubuntuforums.org/showthread.php?p=9411005#post9411005](http://ubuntuforums.org/showthread.php?p=9411005#post9411005)
Now, my Ubuntu LiveCD doesn't load - just holds at the loading screen, so this is an OpenSUSE cd. I got command not found for fsck, e2fsck, and I can't access the hard drive from the liveCD for some reason.

Now, I noticed in the partition editor that a new partition (sda1, 1mb at the front of the disk) had appeared. I had set up the partition setup and hadn't included this. It bumped my root partition to sda2, so I think this may be why it won't boot - because it's trying to do so from sda1. 
I deleted the partition, then got the grub rescue menu. Tried this - 
[http://ubuntuforums.org/showthread.php?p=8954450](http://ubuntuforums.org/showthread.php?p=8954450)
but got command not found for each.

I don't know if my drive is messed up or what. I'm hoping there's a workaround for this, but I'm still really a novice when it comes to this stuff. Thanks in advance for your help!

---

### Post by _rex on 2010-11-10
And I'm a fool. I didn't think to use su then the fsck command while in the OpenSUSE live boot. Retrying some things, but advice is still appreciated - I'm largely in the dark.

---

### Post by _rex on 2010-11-10
Still not getting anywhere. I don't care if I have to reinstall, I just did it so I have everything backed up. I just don't want to have to keep doing it every two days (to my shame, I've done it twice already without posting here). If there's a way to rig the partitioning so this doesn't happen, then I'm prepared to wipe the drive to get it.

---

### Post by oldfred on 2010-11-10
Because it is a Mac does it have gpt partitions?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by _rex on 2010-11-10
Here are the results of the boot info script. In my install I set up the partitions to include sda1 as the root and sda2 as swap, and that's it. Since, it seems like these have been bumped up by one, with a tiny sda1 partition, and some strange sda4 partition added. So yeah, your help is MUCH appreciated - I don't know anything about GPT or whatever the heck is going on here, so thanks!

```
                                                                    
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:      Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:      Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               4,096 1,244,123,134 1,244,119,039  83 Linux
/dev/sda2    *  1,244,123,136 1,250,263,038     6,139,903  82 Linux swap / Solaris
/dev/sda3       1,244,123,136 1,250,263,039     6,139,904  82 Linux swap / Solaris
/dev/sda4                   1             1             1  ee GPT


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System
/dev/sda2           4,096 1,244,123,135 1,244,119,040 Linux or Data
/dev/sda3   1,244,123,136 1,250,263,039     6,139,904 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       6f0f0d69-a104-490c-a91f-78a69ce4307c   ext4                                     
/dev/sda2        414fd261-9692-4709-b743-3cea874ea024   ext4                                     
/dev/sda3        4cfb04e2-d80e-49c6-9c05-6ba861cabd38   swap                                     
/dev/sda: PTTYPE="gpt" 
error: /dev/sda1: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        defaults   (rw,0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 414fd261-9692-4709-b743-3cea874ea024
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 414fd261-9692-4709-b743-3cea874ea024
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 414fd261-9692-4709-b743-3cea874ea024
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=414fd261-9692-4709-b743-3cea874ea024 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 414fd261-9692-4709-b743-3cea874ea024
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=414fd261-9692-4709-b743-3cea874ea024 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 414fd261-9692-4709-b743-3cea874ea024
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 414fd261-9692-4709-b743-3cea874ea024
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=414fd261-9692-4709-b743-3cea874ea024 /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 987.2GB: boot/grub/core.img
 815.4GB: boot/grub/grub.cfg
 649.7GB: boot/initrd.img-2.6.35-22-generic
 987.2GB: boot/vmlinuz-2.6.35-22-generic
 649.7GB: initrd.img
 987.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: Bad file descriptor
hexdump: /dev/sda4: No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: Bad file descriptor
  No volume groups found
mdadm: No arrays found in config file or automatically
```

---

### Post by _rex on 2010-11-10
Ok, so I tried a different partition setup, and tried to use the GPT partition table option, but I'm still not getting anywhere. Anyways, I'm back at the start - what would help me most now would be a walkthrough for setting up a partition setup and installation that would allow me to boot Ubuntu 10.10 on this Macbook consistently. Again, I appreciate the help, truly.

---

### Post by wilee-nilee on 2010-11-10
> **_rex said:**
> Ok, so I tried a different partition setup, and tried to use **the GPT partition table option**, but I'm still not getting anywhere. Anyways, I'm back at the start - what would help me most now would be a walkthrough for setting up a partition setup and installation that would allow me to boot Ubuntu 10.10 on this Macbook consistently. Again, I appreciate the help, truly.

Personally I don't know what this highlighted part means.

Any changes especially like the one you mention, and it still doesn't work post the script again.

Since it is a mac I doubt I can help but the forum member who suggested the script is a quite helpful. You have to kind of hang here to really get it fixed. If you mess around and post scripts and mess around again it makes it very difficult to help you.;) Step back from the computer take a breath and relax.

```
Grub 2 is installed in the MBR of /dev/sda and **looks at sector 2048** of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

```

If you look at the script the actual partition starts at 4096, you will get help just be patient.

---

### Post by srs5694 on 2010-11-10
From the Boot Info Script output, it seems to me you've got two identical MBR partitions (/dev/sda2 and /dev/sda3), which will definitely cause problems. Also, the type-0xEE protective partition is last in the hybrid MBR, which GRUB doesn't like. Before you proceed further, you might want to read some information on the [MBR](http://en.wikipedia.org/wiki/Master_boot_record) and [GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning schemes, as well as their mad-scientist cross, the [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) Also, be aware that Intel-based Macs are EFI-based, but they support a BIOS compatibility mode that's triggered by the presence of a hybrid MBR, or possibly a conventional MBR. This means you've got at least two ways to proceed, assuming you're willing to start from scratch:


[list]
[*]Wipe the GPT data, create a pure-MBR disk, and install just as you would on a commodity PC. This approach should work well if the Mac's EFI kicks into BIOS compatibility mode when it sees a straight MBR configuration. The trick is that some partitioning tools will leave scraps of GPT data when you create a conventional MBR. The simplest approach may be to use GParted from an emergency boot disc and tell it to create a fresh partition table. Specify the type as "msdos", since that's how GParted identifies an MBR partition table. The main drawback to this approach is that you'll have a hard time installing OS X to the disk, should you decide to do so in the future; OS X really wants to install to a GPT disk. For maximum future compatibility, create a 200 MiB FAT partition as the first partition on the disk. If you decide to install OS X later, you can convert the disk to GPT form (with a hybrid MBR, if necessary), and that FAT partition can become the EFI System Partition, which will facilitate OS X installation.
[*]Create a pure GPT configuration *without* a hybrid MBR, and install Ubuntu to this. The trouble is that Ubuntu is not very EFI-friendly, so you'll need to jump through several hoops to get this to work right. Specifically, you'll need to manually create an [EFI System Partition](http://en.wikipedia.org/wiki/EFI_System_partition) (or partition with OS X's Disk Utility, which will create this partition automatically), install Linux, use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert the disk from a hybrid MBR to a straight-GPT configuration (Ubuntu will turn it into a hybrid MBR -- a Bad Move, IMHO), uninstall grub-pc and install grub-efi, reboot using [Super GRUB 2 Disk,](http://www.supergrubdisk.org/) and perhaps tweak your GRUB configuration. It may also be necessary to use an OS X installation disc to "bless" a partition, but I'm still a bit unclear on the precise requirements on this score. I've been experimenting with this sort of setup myself, but I've got to work out the final kinks and write it up in more detail. It may be a couple of weeks before I manage to do this. I've seen reports that this approach sometimes results in poor video performance, but I've had no problems with the Intel 950 video in my Mac Mini 1,1 with this approach. Perhaps other models don't fare so well.
[/list]


My personal preference is to go with a pure-GPT setup; however, this approach is not very well documented, and Ubuntu doesn't seem to support it very well at the moment. If you don't care to be a trailblazer, using an MBR configuration is likely to be simpler, at least at the moment.

---

### Post by _rex on 2010-11-11
Thanks for the help here, srs. I've been doing a little bit of reading up on MBR vs GPT, and I think I'm beginning to grasp it. From what you've said, I think I'll be trying an all-MBR type setup - I don't need OS X, and I'm not yet savvy enough to do much trailblazing, as you say. I'll try see what I can do with it.

---

