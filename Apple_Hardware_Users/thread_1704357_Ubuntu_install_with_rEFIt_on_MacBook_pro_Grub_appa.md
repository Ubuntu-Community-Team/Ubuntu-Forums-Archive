---
title: "Ubuntu install with rEFIt on MacBook pro: Grub apparently messed up my Windows 7 boot"
date: 2011-03-10
forum: Apple Hardware Users
---

### Post by Kaitain on 2011-03-10
This seems to be a variant of a problem many people have had, but after several hours trawling through various forums, I haven't seen a reliable match for my situation.

**In brief:**
Adding a third boot partition (of Ubuntu) to my existing dual boot of OSX 10.6 and Windows 7 seems to have crippled the Windows boot from working, because Grub apparently takes over the process. Yet Grub does *not* appear to be on the Windows partition.

**More verbose:**
I have an older MacBook Pro (3.1, running Snow Leopard) that I recently refitted with a new 240GB SSD HD. With the extra space (it was previously only 120GB) I decided to add a dual boot with Windows 7 using bootcamp. This all went swimmingly well. Encouraged, I decided to follow this Lifehacker article's suggestion and triple-boot the machine with Ubuntu (I'd never used Linux before):

[http://lifehacker.com/#!5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/#!5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

So I now have the nice rEFIt boot partition selection screen, and, indeed, I'm up and running in Ubuntu, and enjoying it.

Only one problem: *I can't get into Windows any more*. If I try to go in through rEFIt *or* by holding down OPT at startup and selecting the windows partition directly, the result is the same: *I get thrown into Grub's selector*, and selecting the Windows partition from there leads to an error message and a dead end. 

Having read through numerous postings, I get the impression that Grub is doing something or living somewhere that it ought not to be, but in most cases I've seen, people had accidentally installed Grub onto the Windows partition (or indeed onto EVERY partition). So far as I can tell, this isn't the case with me. Here's my boot summary:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 283485000 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 314015744.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   273,847,143   273,437,504  af HFS
/dev/sda3         274,110,464   310,370,303    36,259,840  83 Linux
/dev/sda4         310,370,304   314,015,743     3,645,440  82 Linux swap / Solaris


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   273,847,143   273,437,504 HFS+
/dev/sda3     274,110,464   310,370,303    36,259,840 Linux or Data
/dev/sda4     310,370,304   314,015,743     3,645,440 Linux Swap
/dev/sda5     314,015,744   332,816,383    18,800,640 Linux or Data
/dev/sda6     332,816,384   468,860,927   136,044,544 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        c5bee107-051f-385e-8555-0eabcd9552b1   hfsplus    Macintosh HD                  
/dev/sda3        4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3   ext4                                     
/dev/sda4        17c1e3bb-f9de-4584-b43a-a8022f79b8b4   swap                                     
/dev/sda5        71C8-1202                              vfat       SHARED                        
/dev/sda6        CE7A834E7A83326F                       ntfs       BOOTCAMP                      
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=600)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3 ro single 
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
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 4e6b4af7-35b2-46a0-bd0f-6a385e7c18a3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set e57c5db0b8b4f67f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid e57c5db0b8b4f67f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set e57c5db0b8b4f67f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid e57c5db0b8b4f67f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda6)" {
	insmod part_gpt
	insmod ntfs
	set root='(hd0,gpt6)'
	search --no-floppy --fs-uuid --set ce7a834e7a83326f
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda3       /               ext4    errors=remount-ro 0       1
/dev/sda4       none            swap    sw              0       0
/dev/sda3 / ext4 errors=remount-ro,user_xattr 0 1

=================== sda3: Location of files loaded by Grub: ===================


 145.1GB: boot/grub/core.img
 155.6GB: boot/grub/grub.cfg
 142.3GB: boot/initrd.img-2.6.35-22-generic
 143.0GB: boot/initrd.img-2.6.35-27-generic
 145.1GB: boot/vmlinuz-2.6.35-22-generic
 145.1GB: boot/vmlinuz-2.6.35-27-generic
 143.0GB: initrd.img
 142.3GB: initrd.img.old
 145.1GB: vmlinuz
 145.1GB: vmlinuz.old

```

I was considering trying to execute a repair with my Windows 7 CD tonight, but it doesn't seem obvious to me that this would help, given that Grub isn't actually living in that partition.

I've also wondered whether there might be a problem having Windows 7 on a later partition rather than sitting adjacent to the OSX partition. (I resized the OSX downwards so that I could create the small partition for Ubuntu, which sits in the middle and appears as the second option in the rEFIt selection screen.)

Not sure if the boot summary's mention of the core.img file not being located where the system was expecting is of relevance.

Any suggestions gratefully received.

K

---

### Post by srs5694 on 2011-03-10
Your problem is that your Windows partition no longer appears in your [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) Presumably it's been "bumped out" by your Linux partition(s) when you repartitioned for Linux.

Fortunately, the fix is fairly easy (although detail-oriented), but I recommend you read the hybrid MBR page to which I just linked before proceeding:


[list=1]
[*]Download my GPT fdisk (gdisk) from its [Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) (*Do not* install the version in the Ubuntu repositories; that version is ancient and has known bugs.) You can download either the OS X or the Linux version (a .deb file for your architecture, either i386 or amd64); either will work.
[*]Install the GPT fdisk package that you downloaded. Double-clicking should do the job in either OS X or Linux.
[*]Open a Terminal window.
[*]Type "sudo gdisk /dev/sda" (in Ubuntu) or "sudo gdisk /dev/disk0" (in OS X). This will launch gdisk
[*]Type "p" to view your partition table, just as a sanity check. It should show the same partitions that GParted or other utilities show. (Note that OS X's Disk Utility omits the EFI System Partition, though.) If your table looks wrong, exit by typing "q" and investigate further before proceeding.
[*]Type "r" to enter the recovery & transformation menu. The gdisk prompt will change.
[*]Type "h" to create a new hybrid MBR. You'll be prompted to type up to three partition numbers. It looks like you'll want to type either "5 6" or "6 5" -- your Windows and shared-data partitions. You'll be prompted for more information. Tell it to put the 0xEE partition first in the table. Change the type code of the FAT partition to 0c and answer "Y" to the prompt about setting the Windows partition's boot/active flag. There's no point in creating a second protective partition in your case, so tell it not to do so.
[*]When it's done and you get back to the main gdisk prompt, type "o" to view the MBR partition table. It should include the Windows and shared-data partitions (identifiable by their start and end sectors; compare to the "p" output) and a partition of type 0xEE that covers most of the rest of the disk. If this looks wrong, either type "h" to try again or type "q" to quit, research it more, and try again when you better understand it.
[*]Type "w" to save your changes.
[/list]


There's a good chance that Windows will boot from the rEFIt menu at this point, but I can't guarantee that. If it doesn't, see if there's a Windows option in the GRUB menu and, if there is, try to boot using that. Post back with details about what's going wrong. It's possible that adjusting the partitions you include in the hybrid MBR will help Windows boot (Windows is *very* finicky about its boot partition!); or you might need to use the Windows recovery CD/DVD to restore Windows to bootability.

---

### Post by Kaitain on 2011-03-10
Most grateful for the speedy (and detailed) reply.

Will try that tonight and let you know how it goes.

Out of interest, would things have gone any more smoothly had I put Windows on after Linux rather than vice versa?

K.

---

### Post by srs5694 on 2011-03-10
> **Kaitain said:**
> Out of interest, would things have gone any more smoothly had I put Windows on after Linux rather than vice versa?

Probably not, and that would present another pitfall of Windows (perhaps) wiping out the part of GRUB that's installed to the MBR (if in fact that's where you put it). The issue here is that a hybrid MBR can hold only three real partitions, and most tools that create hybrid MBRs just blindly grab the first three partitions they come across for inclusion in the hybrid MBR, without any concern for whether the OSes that actually use those partitions need the partitions to be there. Both OS X and Linux understand GPT, and so don't need their partitions in the hybrid MBR; but because you put the OS X and Linux partitions earlier on the disk than the Windows partitions, it was the OS X and Linux partitions that got included in your hybrid MBR, leaving the Windows partitions (which do need to be there) out in the cold.

FWIW, when you're done, this layout will actually be superior to what you'd have if you'd put the Windows partitions first on the disk. The reason is that your hybrid MBR will contain a protective (type-0xEE) partition that will cover the OS X and Linux partitions. If Windows were first on the disk, the usual hybrid MBR tools would create a hybrid MBR that would include Windows, but you'd then have a big part of the disk that would seem (from Windows) to be unpartitioned, when in fact it would hold Linux and OS X. That opens up the possibility for a disk utility to create "new" MBR partitions in the "unpartitioned" space, thus trashing Linux and/or OS X. With your current layout, that won't be possible -- at least, not without first deleting the 0xEE partition.

---

### Post by Kaitain on 2011-03-10
This is all very informative stuff. Thanks.

To further my understanding of what's happening, are you able to tell me why the Mac's built-in drive selector (holding down opt on restart) displays the Windows partition as an option (one of two, with rEFIt being the others) but is not actually boot to it if selected? Is the MBR misdirecting it when the selection is made?

Also, why does Windows fail to load even when selected as an option from the Grub menu? Is Grub expecting only to be launching a version of Linux?

One other thing: if I wiped out all the Ubuntu and Windows partitions, and then reinstalled Windows 7 from scratch as a second partition, should I expect to have Windows back in working order, or would the MBR still need to be tinkered with?

Thanks again.

---

### Post by srs5694 on 2011-03-10
> **Kaitain said:**
> To further my understanding of what's happening, are you able to tell me why the Mac's built-in drive selector (holding down opt on restart) displays the Windows partition as an option (one of two, with rEFIt being the others) but is not actually boot to it if selected? Is the MBR misdirecting it when the selection is made?

I don't know enough about the Mac's built-in boot selector to answer this authoritatively. My guess, however, is that it's scanning the GPT partitions, finding a Windows installation, and offering to boot it without checking that it's got a valid MBR entry (which it doesn't have). Windows then fails to boot (see below).

> Also, why does Windows fail to load even when selected as an option from the Grub menu? Is Grub expecting only to be launching a version of Linux?

This is a Windows problem, not a GRUB problem. Microsoft refuses to enable their OS to boot on GPT disks on BIOS-based computers, or to support the version of EFI that Apple uses. To boot Windows at all on Macs, Apple has chosen to use a BIOS emulation layer in its EFI. Thus, Macs look like BIOS-based computers to Windows.

This interacts with Microsoft's interpretation of hybrid MBR disks. Unlike Linux and OS X, which give the GPT side precedence, when Windows sees a hybrid MBR disk, it gives the MBR side precedence. Thus, Windows doesn't even know that partitions other than the ones it sees in the MBR exist on the disk. Windows therefore can't boot, since it can't see its own boot partition.

As you may be gathering by now, the ability of Windows to boot on Macs is a rickety house of cards. Remove one card and the whole thing collapses. It's an ugly, ugly hack.

> One other thing: if I wiped out all the Ubuntu and Windows partitions, and then reinstalled Windows 7 from scratch as a second partition, should I expect to have Windows back in working order, or would the MBR still need to be tinkered with?

It depends on how you did it, and I can't even give you detailed instructions on how to do it in a way that would work. IMHO, you're better off following the instructions I gave earlier.

---

### Post by Kaitain on 2011-03-10
Okay. Am typing this from Opera running on Windows. ):P

At first I thought it hadn't worked, because it still threw me into Grub. But now selecting the Windows partition from the list of options in Grub launches Windows successfully. Not QUITE as nice as going there straight from the natty rEFIt menu, but that's like complaining about scratched paintwork when your car's just been repaired for free.

You, sir, are a gentleman and a scholar. I am very grateful.

btw I am assuming (?) that the Windows partition's hex code was to be left at the default value, and only the shared FAT partition's code changed to 0c?

K

---

### Post by srs5694 on 2011-03-11
> **Kaitain said:**
> btw I am assuming (?) that the Windows partition's hex code was to be left at the default value, and only the shared FAT partition's code changed to 0c?

I'm glad it's (mostly) working now. Yes, you should only have changed the FAT partition's type code. The value for the NTFS partition should have been 0x07, which is correct.

As to rEFIt, I'm not sure why it's not working at this point. Perhaps you can dig into the rEFIt configuration files to find some tweak to get it working. I'm afraid that my knowledge of rEFIt is a bit limited, so I can't offer any more specific suggestions.

---

### Post by Kaitain on 2011-03-11
To clarify, the rEFIt menu still appears, and selecting the Apple icon takes me straight through to OSX. But selecting either the Linux or the Windows icon will take me through to Grub, from where I need to make the actual OS selection, i.e. to all intents and purposes the Linux and Windows options jointly constitute a single "Grub" button, and the real choice has to be made via Grub.

I could try reinstalling rEFIt, but at this point I'm not sure I want to tempt fate just for the sake of aesthetics.

---

### Post by srs5694 on 2011-03-11
Ah, I see. It sounds to me like GRUB got installed to the MBR, overwriting the Windows boot loader. Presumably rEFIt is just probing the MBR, and not the Windows boot partition, for boot code, so when it finds code in the MBR, it thinks it's Windows code and gives you a menu option for Windows that launches GRUB. This is speculative, but it fits the facts.

You could probably get it working by re-installing GRUB to the Linux root (/) or (if you've got one) /boot partition and then using Windows utilities to re-install the Windows boot loader to the MBR. There is a risk that by trying this you'd end up damaging the ability to boot one or more OSes, though. Only you can decide if it's worth the risk of trying.

---

### Post by hinckeyboy4jc on 2011-03-11
I had this exact same issue.  I was able to resolve it by booting to the Windows install CD and running the repair options (on Windows 7).  It fixed all of the boot entries and now booting to Mac, Windows and Linux all works perfectly via rEFIt.

---

### Post by danipo on 2011-03-16
Hopefully someone from this thread can help me.  I was having the exact same issue as the first poster.  I initially tried to use the win7 repair disc and use the repair options to fix the boot but it said that it was unable to fix the problems.  I then turned to the poster who had the command line fix.  I initially tried in Linux but after that neither the windows nor the ubuntu partition would boot.  So now I am forced to do it in OSX.  Here is what I am doing so perhaps someone can find my error:

```

Steve$ sudo gdisk /dev/disk0
Password:
GPT fdisk (gdisk) version 0.7.0

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): p
Disk /dev/disk0: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2E89F786-A1C8-4B7E-8B4A-21E2244E7F5A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 268197 sectors (131.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       624470127   297.6 GiB   AF00  CWKS Legia
   3       624734208       640356351   7.4 GiB     8200  Untitled
   4       640358400       786841599   69.8 GiB    0700  Untitled
   5       786843648       976773119   90.6 GiB    0700  BOOTCAMP

Command (? for help): r

Recovery/transformation command (? for help): h

WARNING! Hybrid MBRs are flaky and dangerous! If you decide not to use one,
just hit the Enter key at the below prompt and your MBR partition table will
be untouched.

Type from one to three GPT partition numbers, separated by spaces, to be
added to the hybrid MBR, in sequence: 4 5
Place EFI GPT (0xEE) partition first in MBR (good for GRUB)? (Y/N): y

Creating entry for GPT partition #4 (MBR partition #2)
Enter an MBR hex code (default 07): 0c
Set the bootable flag? (Y/N): y

Creating entry for GPT partition #5 (MBR partition #3)
Enter an MBR hex code (default 07): 
Set the bootable flag? (Y/N): y

Unused partition space(s) found. Use one to protect more partitions? (Y/N): n

Recovery/transformation command (? for help): o

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1    640358399   primary     0xEE
   2      *      640358400    786841599   primary     0x0C
   3      *      786843648    976773119   primary     0x07

Recovery/transformation command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT).
Warning: The kernel may continue to use old or deleted partitions.
You should reboot or remove the drive.
The operation has completed successfully.

```

Thanks for any help.

---

### Post by srs5694 on 2011-03-16
Danipo,

Please be more precise in describing how you're attempting to boot both Windows and Linux and what happens when you do so. For instance, are you selecting the OSes from rEFIt or from GRUB, and what error messages or other displays do you get? If necessary, use a digital camera to photograph the screen and post the images here so we can see them. It might also be worth running the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) and posting the RESULTS.txt file it creates here, although they may not be 100% reliable since rEFIt is an EFI boot loader that (AFAIK) Boot Info Script ignores. (You'll need to boot with a Linux emergency disc to run the Boot Info Script.)

---

### Post by danipo on 2011-03-16
> **srs5694 said:**
> Danipo,

Please be more precise in describing how you're attempting to boot both Windows and Linux and what happens when you do so. For instance, are you selecting the OSes from rEFIt or from GRUB, and what error messages or other displays do you get? If necessary, use a digital camera to photograph the screen and post the images here so we can see them. It might also be worth running the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) and posting the RESULTS.txt file it creates here, although they may not be 100% reliable since rEFIt is an EFI boot loader that (AFAIK) Boot Info Script ignores. (You'll need to boot with a Linux emergency disc to run the Boot Info Script.)

My apologies for not being precise enough.  My problem initially was exactly as described in the very first post and so I assumed that my problem was that I was running the hybrid boot script incorrectly and thus just posted that output.  OSX boots up just fine.  Before when I would select Linux it would bring me to the GRUB menu and and I had a number of choices.  Selecting Ubuntu it would boot up just fine.  If I selected Windows it would show a curser for a second, flash blue really quickly then come up with the message of "no bootable device found....insert bootable disc".  This same thing would happen if I selected Windows.  Reading the first post it sounded like my problem to  a T and so I followed your instructions, I am not sure if I did follow them correctly but exactly what I did is posted above.  Once I did that when I selected either Linux or Windows I would get the "no bootable device found" message.  OSX still boots up just fine though. 

I checked out the boot info script and as I read it I need Linux to run it.  Since I cannot currently boot into Linux and I do not have a live CD with me it is not an option at the moment, perhaps later tonight I can run that if it comes down to it.    Thank you very much for you reply.

---

### Post by Samushighwind on 2011-11-13
> **srs5694 said:**
> Your problem is that your Windows partition no longer appears in your [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) Presumably it's been "bumped out" by your Linux partition(s) when you repartitioned for Linux.

Fortunately, the fix is fairly easy (although detail-oriented), but I recommend you read the hybrid MBR page to which I just linked before proceeding:


[list=1]
[*]Download my GPT fdisk (gdisk) from its [Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) (*Do not* install the version in the Ubuntu repositories; that version is ancient and has known bugs.) You can download either the OS X or the Linux version (a .deb file for your architecture, either i386 or amd64); either will work.
[*]Install the GPT fdisk package that you downloaded. Double-clicking should do the job in either OS X or Linux.
[*]Open a Terminal window.
[*]Type "sudo gdisk /dev/sda" (in Ubuntu) or "sudo gdisk /dev/disk0" (in OS X). This will launch gdisk
[*]Type "p" to view your partition table, just as a sanity check. It should show the same partitions that GParted or other utilities show. (Note that OS X's Disk Utility omits the EFI System Partition, though.) If your table looks wrong, exit by typing "q" and investigate further before proceeding.
[*]Type "r" to enter the recovery & transformation menu. The gdisk prompt will change.
[*]Type "h" to create a new hybrid MBR. You'll be prompted to type up to three partition numbers. It looks like you'll want to type either "5 6" or "6 5" -- your Windows and shared-data partitions. You'll be prompted for more information. Tell it to put the 0xEE partition first in the table. Change the type code of the FAT partition to 0c and answer "Y" to the prompt about setting the Windows partition's boot/active flag. There's no point in creating a second protective partition in your case, so tell it not to do so.
[*]When it's done and you get back to the main gdisk prompt, type "o" to view the MBR partition table. It should include the Windows and shared-data partitions (identifiable by their start and end sectors; compare to the "p" output) and a partition of type 0xEE that covers most of the rest of the disk. If this looks wrong, either type "h" to try again or type "q" to quit, research it more, and try again when you better understand it.
[*]Type "w" to save your changes.
[/list]


There's a good chance that Windows will boot from the rEFIt menu at this point, but I can't guarantee that. If it doesn't, see if there's a Windows option in the GRUB menu and, if there is, try to boot using that. Post back with details about what's going wrong. It's possible that adjusting the partitions you include in the hybrid MBR will help Windows boot (Windows is *very* finicky about its boot partition!); or you might need to use the Windows recovery CD/DVD to restore Windows to bootability.

I did this, and it worked great.  I can now boot Windows from refit.

But now when I boot Linux (which was working perfectly fine earlier), it boots Windows instead.  I did exactly what you said here.  Any ideas?

---

### Post by Samushighwind on 2011-11-16
[http://refit.sourceforge.net/help/linux_boots_windows.html](http://refit.sourceforge.net/help/linux_boots_windows.html)

I found this page which may sort of answer my question, but I'm not really clear on what exactly I do to fix GRUB.  What do I need to use to install GRUB?  Can I do it from Mac or Windows?  Will this be a problem when GRUB receives updates through Linux (which happens, I believe)?

Thanks

---

### Post by pbhound on 2012-02-03
This happened to me as well. i discovered that the problem is because i was creating 4 partitions; 1 for Mac OS X, 1 for Windows, 1 for the Swap partition, and 1 for Ubuntu. now what i did to fix it and actually get the refit menu to work like it is supposed to is to create 3 partitions. 1 partition is Mac OS X, 1 Windows, and the last is the Ubuntu partition. the swap partition can be made as you install Ubuntu. this worked for me i hope it will work for others as well. here is a link to directions on how to install a triple boot on a macbook pro.
[rEFIt Triple boot]("https://help.ubuntu.com/community/MacBook/TripleBoot")

---

### Post by jettechfsr on 2012-03-20
I noticed rEFlt was out of sync started trying to fix MRB and have and GPT with no luck so can some help me out with gsync 


Not sure what happened on my macbook white triple boot using rEFlt lastest version windows 7 says MBR is damaged repair with setup disk and that fails also ever since the Lion upgrade have had lots of problems getting this to triple boot again it would launch grub when I clicked the widows 7 logo but no big deal scroll and launch now I get an error not sure what changed reading above here is my drive wnabted to ask before I changed anything please help

Disk /dev/disk0: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3B18ADDE-44EE-449A-BFC6-CD3880728B0E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 526333 sectors (257.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   0700  EFI System Partition
   2          409640       154845431   73.6 GiB    AF00  CRAIGMAC
   3       155107576       156377103   619.9 MiB   AF00  Recovery HD
   4       156379136       320219135   78.1 GiB    0700  
   5       381659136       386017279   2.1 GiB     8200  
   6       320219136       381659135   29.3 GiB    0700  
  12       386017280       976510983   281.6 GiB   AF00  Storage


Now I'm really messed up here is some more info 


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  Basic Data
 2         409640    154845431  Mac OS X HFS+
 3      155107576    156377103  Mac OS X HFS+
 4      156379136    320219135  EFI System (FAT)
 5      381659136    386017279  Linux Swap
 6      320219136    381659135  Basic Data
 12      386017280    976510983  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1             40       409639  0b  FAT32 (CHS)
 2 *       409640    154845431  af  Mac OS X HFS+
 3      155107576    156377103  af  Mac OS X HFS+
 4      156379136    320219135  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type Basic Data
 Listed in MBR as partition 1, type 0b  FAT32 (CHS)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 155107576:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 156379136:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type EFI System (FAT)
 Listed in MBR as partition 4, type 07  NTFS/HPFS

Partition at LBA 381659136:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Partition at LBA 320219136:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 6, type Basic Data

Partition at LBA 386017280:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 7, type Mac OS X HFS+

---

