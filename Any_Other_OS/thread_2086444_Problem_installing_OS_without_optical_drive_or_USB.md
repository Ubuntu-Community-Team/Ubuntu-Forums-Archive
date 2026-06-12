---
title: "Problem installing OS without optical drive or USB boot option."
date: 2012-11-20
forum: Any Other OS
---

### Post by Gazucha on 2012-11-20
Hola people,

Mods.., hope this is the correct section for this post. Feel free to move if not.

I have been trying to install Peppermint 3 (based on Ubuntu 12.04) onto an old Toughbook CF-28, 30 Gb, 800Mhz, 256Mb Ram, which has no optical drive nor USB boot option. 

After scouring the Web, the general opinion seemed to be to, burn a CD, install the OS onto the HD, whilst it is installed in another machine (with CD/DVD), then plug it back into the desired machine, and off you go...

 I didn't think that was possible but my choices are very limited so I gave it a go...

 Needless to say that didn't work. 

 Although it installed seamlessly using an old Compaq Evo notebook, all I get when I then install the HD back into the CF-28 is a black screen with a small, flashing/blinking white line in the upper left of the screen.

I can enter bios no probs and the boot order is HD, CD, Floppy.

 Does anyone have any idea as to what could be the problem?

I am living in South America and do not have the money to buy a new laptop, nor can I find a CD caddy here and desperately need this laptop for my work. 

Any help would be great...

---

### Post by oldfred on 2012-11-21
Moved to Other OS.

When installing any operating system you have to be sure where boot loader is installed. Did grub get installed to the 30GB drive? Often grub defaults to sda and just installs to an internal drive.

Also video issues could be a concern.

Plug drive back into other system and run Boot-Repair.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:

---

### Post by mips on 2012-11-21
You can do a PXE (network boot) installation on that machine.

---

### Post by NormanFLinux on 2012-11-21
> **Gazucha said:**
> Hola people,

Mods.., hope this is the correct section for this post. Feel free to move if not.

I have been trying to install Peppermint 3 (based on Ubuntu 12.04) onto an old Toughbook CF-28, 30 Gb, 800Mhz, 256Mb Ram, which has no optical drive nor USB boot option. 

After scouring the Web, the general opinion seemed to be to, burn a CD, install the OS onto the HD, whilst it is installed in another machine (with CD/DVD), then plug it back into the desired machine, and off you go...

 I didn't think that was possible but my choices are very limited so I gave it a go...

 Needless to say that didn't work. 

 Although it installed seamlessly using an old Compaq Evo notebook, all I get when I then install the HD back into the CF-28 is a black screen with a small, flashing/blinking white line in the upper left of the screen.

I can enter bios no probs and the boot order is HD, CD, Floppy.

 Does anyone have any idea as to what could be the problem?

I am living in South America and do not have the money to buy a new laptop, nor can I find a CD caddy here and desperately need this laptop for my work. 

Any help would be great...


You can install the free Plop Boot Manager to a very old computer without USB disk and optical boot support. Basically, it will set up a USB flash drive in the BIOS as another virtual hard drive your computer will recognize and then you can do a live boot and install your Linux operating system to your computer's standard hard drive.

Hope this helps!

---

### Post by Gazucha on 2012-11-21
Hi again, thanks for the responses. 

Well, I tried to burn and run Boot-Repair, however, I had to burn it in Widows, (not a spelling mistake, it's what my Wife has become) which means that my Linux Evo doesn't read the DVD. So that idea is currently shelved. 

I have just been trying Plop Boot Manager, however I don't understand the convoluted install instructions.

 [http://www.plop.at/en/bootmanager/thebootmanager.html](http://www.plop.at/en/bootmanager/thebootmanager.html) 

e.g.  I get section 1...  

Section 2... Which main menu? Where? 

etc. etc.      


Not including many previous wasted days without success, I have already spent the last 4 entire days and evenings on this and I actually consider my life to be more valuable than to live as a computer Geek (although maybe I'm wrong).    

Does no-one use plain-English instructions within the Linux community?   

My internet connection is constantly being disrupted just to make my life easier. 

I also had a look at the PXE, and didn't understand that either. Do I have to register somewhere? which files do I load, where? and how? or do I need an external HD? 

These and other questions shall be answered shortly....

 Patience is a virtue.  

Thanks again.

---

### Post by mips on 2012-11-22
Just write the plpbtin.img as a IMAGE (don't just copy it across) to a floppy disk (I think your laptop has one of those) and boot off it. Once it has loaded just tell it to boot from your usb or cd-rom drive.

What OS do you currently have access to to write that plpbtin.img image with and I could try and give you more detailed instructions on how to write it to a floppy.

---

### Post by kiyop on 2012-11-22
> **oldfred said:**
> when installing any operating system you have to be sure where boot loader is installed. Did grub get installed to the 30gb drive? Often grub defaults to sda and just installs to an internal drive.

Also video issues could be a concern.
+1

> **mips said:**
> Just write the plpbtin.img as a IMAGE (don't just copy it across) to a floppy disk (I think your laptop has one of those) and boot off it. Once it has loaded just tell it to boot from your usb or cd-rom drive.
Gazucha, do you have USB-CD drive or USB-flash?
If you installed peppermint correctly onto the HDD, I suggest you to use Super Grub2 Disk.
It can be written to a floppy disk also.
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

---

### Post by ugm6hr on 2012-11-22
> **Gazucha said:**
> Although it installed seamlessly using an old Compaq Evo notebook, all I get when I then install the HD back into the CF-28 is a black screen with a small, flashing/blinking white line in the upper left of the screen.

Is the old Compaq Evo still working the same? What OS did / does that have installed? When you installed on this HD, did you replace the existing drive for the new one?

The issue of where "Grub" (bootloader) was installed when you initially installed Ubuntu on the Evo is important. The answers to the above questions may help us work that out.

If you don't understand any of this, then you are likely going to struggle. Remember, most people do not install any OS ever, and installing without bootable media is even harder.

---

### Post by Gazucha on 2012-11-23
First, This is NOT how I wrote it, BUT 6 TIMES EDITING this, seems to have NO effect!!!!!!!!!!!!   thanks to you all for your time and contributions.      Hi Mips... absolutely no Floppy Drive in the area, but thanks for the thought.       Kiyop,   No USB CD-drive nor USB-Flash. :(         UGM6HR,  Compaq is working sweet (writing to you now)...    didn't install on THIS hard drive. Replaced with another.       KInda like the sound of SuperGrub 2 Disk. I'll have a look.       USB 2.0, CD/DVDRW, PCMCIA etc.  Running Mint 13 'Maya' Mate edition. No problems...  ,internet via Network cable, 3 External Hard drives and various USB data keys free to use...         It's not that I don't understand anything, I just needed a break and as we all know, after too long at the desk, info' just stops making sense.      Had today and yesterday off.   Ready to absorb information again. :)       I don't believe this is beyond resolution or I would never have started.

---

### Post by kiyop on 2012-11-24
Thanks for your reply.
[quote=Gazucha]      Kiyop,   No USB CD-drive nor USB-Flash.[/quote]
So, you need not use PLoP boot manager.
Super Grub2 disk (floppy) is better.
Can you connect the problematic HDD, which is now connected to Toughbook CF-28, to correctly working Compaq Evo?
If you can, please confirm that there is a partition which contains /boot, /dev and /home directories in the problematic HDD.
If you can run boot info script, execute it while the problematic HDD is connected, and post the contents of the generated RESULTS.txt between "[ code]" and "[ /code]" (please omit the spaces just after "[").
You can get boot info script at  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And as oldfred pointed out, you can use Boot Repair, although I am not familiar with it.

---

### Post by ugm6hr on 2012-11-24
@Gazucha
I suspect there must be a driver issue causing issues between the 2 computers.

PXE / network install should be a possibility, if the BIOS allows this - do you have a network boot option in BIOS?

Otherwise, I think this may be worth trying: use unetbootin (or similar) to install a "LiveHD" version on a partition; boot from liveHD version to install on to the main / primary partition.

This would be achieved by:
Place HD into Evo.
Boot Evo from another drive / live USB
Partition HD with a 2GB partition towards back of drive
Launch unetbootin (on LiveUSB)
Install iso to 2GB partition on HD - as "liveHD"
Transfer HD to Toughbook
Try booting Toughbook - it should boot to the LiveHD
This should allow you to install to the main HD partition while in the Toughbook.

I have never tried doing something like this - but I cannot see why it wouldn't work. Perhaps wait for others to comment before attempting.

---

### Post by Gazucha on 2012-11-26
Hi again,
 ok, Kiyop,

Ran bootinfoscript and the output is here...

[http://pastebin.com/SJKiMvgm](http://pastebin.com/SJKiMvgm)

To edit... the link has no info and the results page is surely too long to post here?   

But as I know not how to do otherwise, here it is...

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Peppermint Three
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    54,411,263    54,409,216  83 Linux
/dev/sda2          54,413,310    58,603,519     4,190,210   5 Extended
/dev/sda5          54,413,312    58,603,519     4,190,208  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d21626cb-5189-4b3f-9537-bccdf5fbbe24   ext4       
/dev/sda5        a84d29c6-a563-4cae-b094-d0bcc0800722   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root d21626cb-5189-4b3f-9537-bccdf5fbbe24
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root d21626cb-5189-4b3f-9537-bccdf5fbbe24
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Peppermint, with Linux 3.2.0-23-generic' --class peppermint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d21626cb-5189-4b3f-9537-bccdf5fbbe24
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=d21626cb-5189-4b3f-9537-bccdf5fbbe24 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Peppermint, with Linux 3.2.0-23-generic (recovery mode)' --class peppermint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d21626cb-5189-4b3f-9537-bccdf5fbbe24
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=d21626cb-5189-4b3f-9537-bccdf5fbbe24 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d21626cb-5189-4b3f-9537-bccdf5fbbe24
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d21626cb-5189-4b3f-9537-bccdf5fbbe24
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d21626cb-5189-4b3f-9537-bccdf5fbbe24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a84d29c6-a563-4cae-b094-d0bcc0800722 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.286479950 = 2.455089152    boot/grub/core.img                             1
  22.523292542 = 24.184201216   boot/grub/grub.cfg                             1
   1.032226562 = 1.108344832    boot/initrd.img-3.2.0-23-generic               2
  22.519691467 = 24.180334592   boot/vmlinuz-3.2.0-23-generic                  1
   1.032226562 = 1.108344832    initrd.img                                     2
  22.519691467 = 24.180334592   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt

---

### Post by Gazucha on 2012-11-26
Thanks ugm6hr,
 
 I'll try that. Although it already has a 2.1Gb Extended Partition on top of a 2.1Gb Swap space. 

Actually writing to you via the Peppermint 3 hard drive installed in the Evo.

Is it wise to partition this HD whilst running the OS?

I suppose I'm about to see? :)

---

### Post by Gazucha on 2012-11-26
Well, first I ran Boot-Repair.

The output file is allegedly here...

[http://paste2.org/p/2526683](http://paste2.org/p/2526683)

I've had success with BR before, with another system and different 'issue'.

Gonna switch it back and see what happens.

---

### Post by Gazucha on 2012-11-26
Hi again chaps...  re-installed the HD with Peppermint (and new 2gb partition with PM ISO) back into the Toughbook, however no joy. Just a blank screen with flashing cursor after the Panasonic logo and Boot/Bios options.  Less than a month til the end of the World and there go few more hours of my life...  :)

---

### Post by oldfred on 2012-11-26
I do not see your model on this site, and most have nothing posted yet. This one says it has the same touch screen as yours? And has some specific suggestions on video drivers.

[http://www.linlap.com/panasonic_toughbook_72](http://www.linlap.com/panasonic_toughbook_72)

---

### Post by ugm6hr on 2012-11-27
> **Gazucha said:**
> Hi again chaps...  re-installed the HD with Peppermint (and new 2gb partition with PM ISO) back into the Toughbook, however no joy. Just a blank screen with flashing cursor after the Panasonic logo and Boot/Bios options.  

Not sure how experienced you are - so sorry if I'm being patronising...
But did you try booting the drive in the Evo after creating the LiveHD partition?
It would be helpful to know if the LiveHD works on hardware we know that can run Linux.

---

### Post by kiyop on 2012-11-27
Thanks for posting the contents of the RESULTS.txt. :)

I found nothing wrong in the reported boot sequence.
So, I wonder if the BIOS of your problematic PC cannot use partition which reaches a certain limit from the first sector.
In such case, you can make small /boot partition from the beginning of the HDD separately from / partition.
At installation, make a small /boot partition from the beginning of the HDD.

---

### Post by Gazucha on 2012-11-27
ugm6hr,   But did you try booting the drive in the Evo after creating the LiveHD partition?
 Yeah, tried that first, and all went well.   Thanks again for all your time.

---

### Post by Gazucha on 2012-11-27
> **oldfred said:**
> I do not see your model on this site, and most have nothing posted yet. This one says it has the same touch screen as yours? And has some specific suggestions on video drivers.

[http://www.linlap.com/panasonic_toughbook_72](http://www.linlap.com/panasonic_toughbook_72)

  Cheers Fred,  Cool link.. Should help later :)

---

### Post by Gazucha on 2012-11-27
> **kiyop said:**
> Thanks for posting the contents of the RESULTS.txt. :)

I found nothing wrong in the reported boot sequence.
So, I wonder if the BIOS of your problematic PC cannot use partition which reaches a certain limit from the first sector.
In such case, you can make small /boot partition from the beginning of the HDD separately from / partition.
At installation, make a small /boot partition from the beginning of the HDD.

  Hola amigo,   don't mean to be thick, but could you clarify please?  Which size is 'small'?  Which program is best to do this task?  And when exactly is 'at installation?' What is also the difference between a 'boot' and 'non-boot' partition?  Thanks again for your time.   Hasta luego,

---

### Post by ugm6hr on 2012-11-27
> **Gazucha said:**
> ugm6hr,   But did you try booting the drive in the Evo after creating the LiveHD partition?
 Yeah, tried that first, and all went well.   Thanks again for all your time.

If you truly booted into the LiveHD Peppermint (**and not just the same already installed Peppermint** - the LiveHD should behave identically to the LiveUSB - and not require login etc) on the Evo - then the issue is with hardware compatibility on Toughbook. 

If true, it may be necessary to use the "alternative" install CD (or equivalent) to try and install, if the live OS will not boot.

Else, it may be that your hardware just doesn't have Linux drivers at all.

Judging by one person's experience of your graphics card (specs from [http://www.linlap.com/panasonic_toughbook_72](http://www.linlap.com/panasonic_toughbook_72) )...
[http://www.markturner.net/2012/05/08/ubuntu-12-04-disappoints/](http://www.markturner.net/2012/05/08/ubuntu-12-04-disappoints/)
You may be out of luck.

---

### Post by kiyop on 2012-11-27
To Gazucha,

Read the above post of ugm6hr first.

Of course, the above written guess of mine may be wrong. If my guess is wrong, excuse me.

I answer to your questions:
[quote=Gazucha]Which size is 'small'?[/quote]
It depends on the BIOS. Refer to
[http://www.dewassoc.com/kbase/hard_drives/resolving_drive_barriers.htm](http://www.dewassoc.com/kbase/hard_drives/resolving_drive_barriers.htm)
/boot partition should contain only kernels and initramfs files of peppermint, and files required for kernel loader (such as grub2).
So, maybe the necessary size of /boot partition is less than 100MB.

[quote=Gazucha]Which program is best to do this task?[/quote]
I guess that Peppermint installer can partition the HDD.

[quote=Gazucha]And when exactly is 'at installation?'[/quote]
Connect the HDD (which will be connected to Toughbook) to Evo.
Boot Peppermint Installation USB/DVD/CD.
At installation of Peppermint, you can partition.

[quote=Gazucha]What is also the difference between a 'boot' and 'non-boot' partition?[/quote]
I could not find a good link, but refer to
[http://linuxmafia.com/~karsten/Linux/FAQs/partition.html]("http://linuxmafia.com/%7Ekarsten/Linux/FAQs/partition.html")

Can you create a bootable floppy?
Can you boot any OS on the problematic Toughbook now?

---

### Post by Gazucha on 2012-11-27
Hang on,   No, I didn't boot into the Live CD.. I'll get back to you...

---

### Post by Gazucha on 2012-11-27
Sheesh! they don't help by all using different HD caddy's...  Anyway, NO, it is NOT booting from the Live CD partition.. It doesn't even show it at boot.  Now what?  Can't we just start again? Fresh install using the Evo?  Everyone seems to think it should work.. Maybe I used the wrong Partition type or something?  Answers to...  Can you create a bootable floppy? Can you boot any OS on the problematic Toughbook now?   No Floppy anything...  No OS on the Toughbook...  Gonna try to install PMint again...

---

### Post by Gazucha on 2012-11-27
Why do some of my posts lack any spacing????????????????????  THAT is an irritating technical glitch!

---

### Post by Gazucha on 2012-11-27
And why must I sign in  (almost) EVERY time I write a Post?

---

### Post by Gazucha on 2012-11-27
Mmmm! May have found the problemo..  From the official Panasonic pages.  [https://www.panasonic.com/business/toughbook/computer-support-faqs-28.asp](https://www.panasonic.com/business/toughbook/computer-support-faqs-28.asp)   THIS quote...  &quot; What operating systems can I install on the CF-28?   Depending on the mark or generation of the CF-28, the following operating systems may be supported: Windows NT, Windows 98, Windows 2000 and Windows XP Professional.&quot;    Sounds to me like Game Over.   I flatly refuse to demean my very existence by the retarded motion of ever again using any product of the evil Bill Hates (he who promotes the W.H.O. depopulation and the Geo-Engineering programs).    The &quot;problematic&quot; Toughbook shall now be sold to a Widows retard   Thank you all for your time.    Hopefully we have all learned something?

---

### Post by ugm6hr on 2012-11-27
> **Gazucha said:**
> What operating systems can I install on the CF-28?   Depending on the mark or generation of the CF-28, the following operating systems may be supported: Windows NT, Windows 98, Windows 2000 and Windows XP Professional

This does not necessarily mean you can't install Linux. In fact, almost every laptop ever sold (except Macs) will have a similar description.

However, it does sound like the CF-28 is difficult to get Ubuntu (or any recent Linux) on.
[http://ubuntuforums.org/showthread.php?t=1008894](http://ubuntuforums.org/showthread.php?t=1008894)
[http://nobles.wordpress.com/2008/12/07/list-of-linux-distros-tested-on-cf-28-toughbook/](http://nobles.wordpress.com/2008/12/07/list-of-linux-distros-tested-on-cf-28-toughbook/)
[http://byrd740.wordpress.com/2009/09/20/linux-on-panasonic-cf-28/](http://byrd740.wordpress.com/2009/09/20/linux-on-panasonic-cf-28/)
[http://www.digriz.org.uk/debian/panasonic/cf28](http://www.digriz.org.uk/debian/panasonic/cf28)

I can't see any mention of any successful installs since 2009. Except:
[http://www.edubuntu.org/deployments](http://www.edubuntu.org/deployments)

21/11/2012 update shows use of CF-28 as thin clients, which would suggest that the graphics card IS supported by 12.04.

Your choice if you want to try for longer - there is no guarantee of success, but it is likely you can install linux, assuming all CF-28 have the same graphics card.

Happy to help guide you through, since it appears you are in fact a beginner with Linux OS installations.

---

### Post by kiyop on 2012-11-28
As ugm6hr mentioned, there may be difficulty in installing current versions of many linux distributions.

But your problem may be solved by writing proper lines in /etc/X11/xorg.conf.

I suggest you to install debian:

As ugm6hr linked, two guys selected debian:

[http://www.digriz.org.uk/debian/panasonic/cf28](http://www.digriz.org.uk/debian/panasonic/cf28)
(although finally he selected xubuntu)

[http://byrd740.wordpress.com/2009/09/20/linux-on-panasonic-cf-28/](http://byrd740.wordpress.com/2009/09/20/linux-on-panasonic-cf-28/)

If you want to install debian on it, how about posting to debian forum:
[http://forums.debian.net/](http://forums.debian.net/)
Many unkind but clever guys will answer to you, I hope. ;)

---

### Post by Gazucha on 2012-11-29
Hola Kiyop, Ugm6hr and the rest of the world,  thank you again for your time..  Here's the news.  T'other evening, I re-installed the O/S without being on-line (to install updates etc.) and then booted whilst holding down the 'Shift' key.   We then had the word "GRUB" appear, instead of the flashing cursor. Unfortunately THAT was it. Progress, but not much. So tried that a couple more times (to check) and then gave up and carried on reading my book, - although without switching the T-Book off-  About an hour later, long after I think the machine is fast asleep, the screen suddenly returns to life with, get this...  THE FULL BOOT MENU!!!!!!!!!!!!!  I know, I know... but calm down, coz when I selected Boot P-Mint normally... it didn't boot. In fact it never again even reached the Grub menu.. Just the word "GRUB" when I hold shift.  But the moral of the story is. Patience!     BTW.   Boot info script said...   sda1: __________________________________________________________________________  File system: ext4 Boot sector type: - Boot sector info: Operating System: Peppermint Three Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda2: __________________________________________________________________________  File system: Extended Partition Boot sector type: - Boot sector info:  sda5: __________________________________________________________________________  File system: swap Boot sector type: - Boot sector info:  ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 30.0 GB, 30005821440 bytes 255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition Boot Start Sector End Sector # of Sectors Id System  /dev/sda1 * 2,048 54,411,263 54,409,216 83 Linux /dev/sda2 54,413,310 58,603,519 4,190,210 5 Extended /dev/sda5 54,413,312 58,603,519 4,190,208 82 Linux swap / Solaris   "blkid" output: ________________________________________________________________  Device UUID TYPE LABEL  /dev/sda1 e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d ext4 /dev/sda5 a84d29c6-a563-4cae-b094-d0bcc0800722 swap  ================================ Mount points: =================================  Device Mount_Point Type Options  /dev/sda1 / ext4 (rw,errors=remount-ro)   =========================== sda1/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then set have_grubenv=true load_env fi set default="0" if [ "${prev_saved_entry}" ]; then set saved_entry="${prev_saved_entry}" save_env saved_entry set prev_saved_entry= save_env prev_saved_entry set boot_once=true fi  function savedefault { if [ -z "${boot_once}" ]; then saved_entry="${chosen}" save_env saved_entry fi }  function recordfail { set recordfail=1 if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video { insmod vbe insmod vga insmod video_bochs insmod video_cirrus }  insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d if loadfont /usr/share/grub/unicode.pf2 ; then set gfxmode=auto load_video insmod gfxterm insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d set locale_dir=($root)/boot/grub/locale set lang=en_US insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ]; then set timeout=10 else set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### function gfxmode { set gfxpayload="${1}" if [ "${1}" = "keep" ]; then set vt_handoff=vt.handoff=7 else set vt_handoff= fi } if [ "${recordfail}" != 1 ]; then if [ -e ${prefix}/gfxblacklist.txt ]; then if hwmatch ${prefix}/gfxblacklist.txt 3; then if [ ${match} = 0 ]; then set linux_gfx_mode=keep else set linux_gfx_mode=text fi else set linux_gfx_mode=text fi else set linux_gfx_mode=keep fi else set linux_gfx_mode=text fi export linux_gfx_mode if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi menuentry 'Peppermint, with Linux 3.2.0-23-generic' --class peppermint --class gnu-linux --class gnu --class os { recordfail gfxmode $linux_gfx_mode insmod gzio insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d linux /boot/vmlinuz-3.2.0-23-generic root=UUID=e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d ro quiet splash $vt_handoff initrd /boot/initrd.img-3.2.0-23-generic } menuentry 'Peppermint, with Linux 3.2.0-23-generic (recovery mode)' --class peppermint --class gnu-linux --class gnu --class os { recordfail insmod gzio insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d echo 'Loading Linux 3.2.0-23-generic ...' linux /boot/vmlinuz-3.2.0-23-generic root=UUID=e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d ro recovery nomodeset echo 'Loading initial ramdisk ...' initrd /boot/initrd.img-3.2.0-23-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d linux16 /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d linux16 /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries. Simply type the # menu entries you want to add after this comment. Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f $prefix/custom.cfg ]; then source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sda1/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # #       proc /proc proc nodev,noexec,nosuid 0 0 # / was on /dev/sda1 during installation UUID=e4babbe5-fcb8-42b5-8ab5-be6015c5dc1d / ext4 errors=remount-ro 0 1 # swap was on /dev/sda5 during installation UUID=a84d29c6-a563-4cae-b094-d0bcc0800722 none swap sw 0 0 /dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0 --------------------------------------------------------------------------------  =================== sda1: Location of files loaded by Grub: ====================  GiB - GB File Fragment(s)  22.516281128 = 24.176672768 boot/grub/core.img 1 0.131896973 = 0.141623296 boot/grub/grub.cfg 1 0.756328583 = 0.812101632 boot/initrd.img-3.2.0-23-generic 2 4.244575500 = 4.557578240 boot/vmlinuz-3.2.0-23-generic 1 0.756328583 = 0.812101632 initrd.img 2 4.244575500 = 4.557578240 vmlinuz 1  =============================== StdErr Messages: ===============================  xz: (stdin): Compressed data is corrupt      Boot-repair is here...  [http://paste2.org/p/2532187](http://paste2.org/p/2532187)

---

### Post by kiyop on 2012-11-30
I have never used peppermint. I found that peppermint uses cloud technology and run applications over network (internet). Thus, I wonder if peppermint tries to find internet connection at boot time, which may take long time.
If you can get into Grub2 menu by pressing "Shift" key at boot time, press "e" key to enter into command line.
Remove "quiet" and "splash" if it/they are in the line starting with "linux".
Press "Ctrl" and "x" key at the same time to start booting.
Then I hope some log and error messages will be displayed on the screen.

I really hate "quiet" and "splash".
Some developers may think that beautiful splash screen without log messages looks cool for newbies, but if there are some errors and if they cannot boot correctly, beautiful splash screen without log messages prevents them from trying installation.

I also wonder if the size of the memory; 256MB is not enough to run peppermint 3 fast.
On peppermint HP: [http://peppermintos.com/guide/install/](http://peppermintos.com/guide/install/)
> The absolute minimum required specs are as follows: 
[LIST]
[*]192 MB of RAM
[*]Processor based on Intel x86 architecture
[*]At least 2 GB of available disk space
[/LIST]
Again I suggest you installing debian. I could install debian by netinstall to a virtual guest circumstances with only 55MB of assigned RAM.
I installed debian onto a real notebook PC with 128MB RAM. On the installed debian, I can watch videos on internet by using iceweasel (firefox).
You can refer to: [http://www.debian.org/releases/stable/i386/ch03s04.html.en](http://www.debian.org/releases/stable/i386/ch03s04.html.en)

To tell the truth, I cannot understand why you try to install peppermint 3 onto such low spec PC.

---

### Post by Gazucha on 2012-11-30
I also wonder if the size of the memory; 256MB is not enough to run  To tell the truth, I cannot understand why you try to install peppermint 3 onto such low spec PC.[/QUOTE]

  In fact I was mistaken. The Ram is 512Mb.  I shall try your suggested boot ideas tomorrow but  Thankyou once more for your time. Maybe Debian is calling. Can you suggest a particular release?   Hopefully this post won't appear as continuous text and hopefully I shan't have to sign in again..  :)

---

### Post by kiyop on 2012-12-01
> **Gazucha said:**
> The Ram is 512Mb.
I see. Thanks for reporting. :)

> **Gazucha said:**
> Maybe Debian is calling. Can you suggest a particular release?
As for stable (squeeze), testing (wheezy) and unstable (sid), read: 
[http://www.debian.org/releases/](http://www.debian.org/releases/)

My way of installing only necessary packages in debian is not like usual installation method.
Does your computer like Evo have wired internet port for LAN cable?
If so, maybe you can use my way.
If you want to install debian on Toughbook, please let me know.

---

### Post by viper250 on 2012-12-02
> **mips said:**
> You can do a PXE (network boot) installation on that machine.

if you are connected to a hub or router you can use a regular ethernet cable and do a net install. 
to connect 2 computers directly without a hub or router you would need a crossover cable.

---

### Post by Gazucha on 2012-12-04
Apologies for the delayed response.  Just needed a break from this,   #I have a cable internet connection and a network pcmcia card.  I'm up for trying anything.. Just need to know how?  and Kiyop,  "As for stable (squeeze), testing (wheezy) and unstable (sid), read: [http://www.debian.org/releases/](http://www.debian.org/releases/)  My way of installing only necessary packages in debian is not like usual installation method. Does your computer like Evo have wired internet port for LAN cable? If so, maybe you can use my way. If you want to install debian on Toughbook, please let me know. "  Yeah, I'm up for installing Debian if you wanna help. :)

---

### Post by kiyop on 2012-12-06
> **Gazucha said:**
> I'm up for installing Debian if you wanna help. :)
I do not want to help you of my free will.;)
I am willing to help you if you want me to help you.

I hope that debian kernel such as [http://ftp.nara.wide.ad.jp/pub/Linux/debian/dists/stable/main/installer-i386/current/images/netboot/debian-installer/i386/linux](http://ftp.nara.wide.ad.jp/pub/Linux/debian/dists/stable/main/installer-i386/current/images/netboot/debian-installer/i386/linux)  and initramfs such as [http://ftp.nara.wide.ad.jp/pub/Linux/debian/dists/stable/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz](http://ftp.nara.wide.ad.jp/pub/Linux/debian/dists/stable/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz) can detect, can use your network card and can connect to internet.

First, configure BIOS of Toughbook so that the first booting media is the internal HDD. 

Connect the HDD for Toughbook to Evo and boot any live linux which contains partitioning tool such as gparted and grub2 from CD. Start the partitioning tool. Make a new ms-dos partition table on the HDD. Make a small (around 200MB) ext2 partition from the beginning of the HDD. Execute
```
fdisk -l
```with root privilege to find the device file name of the HDD such as /dev/sda and to find that of the partition such as /dev/sda1. If you can use sudo in the booting live linux, instead of the above,
```
sudo fdisk -l
```If the device file name of the HDD is /dev/sda and that of the partition is /dev/sda1, execute with root privilege,
```
mkdir /mnt2
mount -t ext2 /dev/sda1 /mnt2 -o rw
grub-install --root-directory=/mnt2 /dev/sda
grub-mkconfig -o /mnt2/boot/grub/grub.cfg
```Copy the above two files (kernel and initramfs) on the partition (mounted at /mnt2).
```
chmod +w /mnt2/boot/grub/grub.cfg
nano /mnt2/boot/grub/grub.cfg
```and add the following lines just before the line "### END /etc/grub.d/40_custom ###":
```
menuentry "debian net install" {
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
linux /linux
initrd /initrd.gz
}
```And press "CTRL" and "o" to save.
Press "CTRL" and "x" to finish nano (editor).
Then execute
```
sync
umount -l /mnt2
```FInally, shutdown the live linux and place the HDD back to the original Toughbook. Boot Toughbook. At grub2 screen, select "debian net install".
God bless you!

---

### Post by Gazucha on 2012-12-10
Hi again Kiyop,  thanks for the input... I've been away these last 5 days but will give your suggestions a shot as soon as I have some free time (lots of work also suddenly arrived).   Will let you know.

---

### Post by Gazucha on 2013-06-04
Hello again UbuntuWorld...

Apologies for disappearing...

 so, the latest is.. 

 took the plunge last January and bought a brand new Panasonic DVD CDRW internal drive and just planned to load Windows and sell the problematic CF28.

How hard can that be, right? 

So... 5 months later...

 it has still not been possible to install any Linux, nor XP English XP Brazil nor Win2000. These last few days been trying to install Mint 11 LXDE 32-bit and every time was having the install hang right at the end, citing something about in-out problems - Panasonic errno 5 (error no 5). It said to check the DVD and the checksum.

 Today downloaded a new copy but for the life of me could not understand the instructions to check the DVD's MD5 so just chucked it in the CF28 and hoped for the best. Also changed the CF 28 DVD rom just to check.

 Now it hangs before it starts, quoting... 

"...BusyBox v1:1.17.1  (ubuntu 1:1.17.1-10ubuntu) built-in shell (ash)
  Enter 'help' for a list of built-in commands

 (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
 Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 udevd[73] : worker [160] unexpectedly returned with status 0x0100

 udevd[73] : worker [160] failed while handling '/devices/virtual/block/loop0 "


 ?? so what does that mean??

 I would honestly like to chuck it under a bus... But it's a floopin Toughbook innit? Probably like it?  !! ??!!!

---

### Post by Gazucha on 2013-06-04
Ok, tried installing from the old Mint 11 LXDE dvd and this time it stalled slightly earlier, during the Keyboard layout setup. But at least this DVD opens... So I would assume that rules out DVD Rom problem? I have one more that I can test just to be sure.
 
 The exact quote is as follows.

" The installer encountered an error copying files to the Hard Disk:

  [Errno 5] Input/output error

 This is often due to a faulty CD/DVD drive disk or drive, or a faulty
 hard disk. It may help to clean the CD/DVD, to burn the CD/DVD
 at a lower speed, to clean the CD/DVD drive lens (cleaning kits
 are often available from electronic suppliers), to check whether
 the hard disk is old and in need of replacement, or to move the 
  system to a cooler environment. "

 Hang on... there's a bus coming.....

---

### Post by Gazucha on 2013-06-04
So did a longer search and found this workaround.. for the BusyBox issue...

[http://www.hacktohell.org/2011/07/fixing-can-not-mount-devloop0-while.html#.Ua4ekSziowU](http://www.hacktohell.org/2011/07/fixing-can-not-mount-devloop0-while.html#.Ua4ekSziowU)

General Error format ...
[INDENT] [B]BusyBox vX.XX.X(Ubuntu X:X.X.X-XXXXXX) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs[/B][/INDENT]
This error is really frustrating and after googling for a looong time I still had no fix :(

but then I found out that by not mounting the drives when ubuntu booted up , this can be stopped !

First in the menu that appears , select Default and press Tab .

Change this[INDENT] ***initrd=/ubninit file=/preseed/ubuntu.seed boot=casper quiet splash --***
[/INDENT]
to[INDENT] [I][B]initrd=/ubninit file=/preseed/custom.seed boot=casper nohd --
[/B][/I]


p.s. (don't miss the 'custom')
[/INDENT]

  It is loading as we speak. :)

 Fingers crossed.

---

### Post by Gazucha on 2013-06-04
Back at the Bus Stop....

 That didn't work although most likely as my code from pressing Tab was different. I received this ....

 ***/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet splash --***

which I alternately changed to;

 ***/casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.lz nohd --***

and 

 ***/casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper nohd --***

The latter having the greater effect, running through loads of script before eventually stalling, saying that initrd was missing (or something similar).

---

### Post by Gazucha on 2013-06-04
Tried again without including the 'custom'..

 It ran and stalled with this message.

[I][B]......................................................
Ready.
This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.[/B][/I]

 

That surely means wrong OS version? 64 instead of 32 bit. But there is ONLY 32 bit for Mint 11 LXDE. 

Could it because I burnt it to a DVD RW and not a CD R?

---

### Post by Gazucha on 2013-06-04
Ok, burnt a Mint 9 LXDE 32-bit, which just hangs on the Isolinux ..3.36.. etc.etc.etc.etc PeterAnvin et al... Checked it another 64-bit PC and booted first time. So changed my CF28 DVD Rom again.. no change..


 COULD IT BE THE BIOS VERSION IS SCREWED IN THE CF28???

 I can run it all day long off of CD's but cannot install a sausage!

 Still at the bus stop.....

---

### Post by Gazucha on 2013-06-05
Ok, so installed a Macbook Superdrive n the CF28 caddy and got back to installing the entire OS. All goes well until I reboot after "successful install " but when I reboot I still get the flashing, blinking white line in the top left of the screen....

 It was that little line that started this whole thread off, six months ago.

Which points to a Boot Problem no?

 Anyone know how to check for Boot problems?

---

### Post by oldfred on 2013-06-06
Flashing cursor is often video issue. What video card/Chip? It may have booted past grub and just not able to load a driver, if not video possibly another driver.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Gazucha on 2013-06-06
Ok cool, 

thanks for the reply Fred.

Not sure right here and now about the Video card/chip i.d. but it could be our culprit. Although until I nuked the HD with Dban, the XP previously installed had never missed a beat!? 

I must say I am intrigued, as I can run any Linux OS forever, just from the CD/DVD, and even with the Windows installs it often boldly states, that it "installed without problem" however we just can't seem to boot past that cursor from the HD (and I have tried 5 different HD's!)

 Gotta pop out for some dog food, but I'll check out your links and report back.

---

### Post by ronniew on 2013-06-06
> **Gazucha said:**
> Ok cool, 

thanks for the reply Fred.

Not sure right here and now about the Video card/chip i.d. but it could be our culprit. Although until I nuked the HD with Dban, the XP previously installed had never missed a beat!? 

I must say I am intrigued, as I can run any Linux OS forever, just from the CD/DVD, and even with the Windows installs it often boldly states, that it "installed without problem" however we just can't seem to boot past that cursor from the HD (and I have tried 5 different HD's!)

 Gotta pop out for some dog food, but I'll check out your links and report back.

try using [gdiskdump]("https://launchpad.net/gdiskdump") or [pendrive linux]("http://www.pendrivelinux.com") to make the usb, it does it using dd instead of the way unetbootin or startupdiskcreator do..... this is my solution when i get troublesome iso's


forgot to add if you can't boot from usb [just use plop]("http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/")

---

### Post by Gazucha on 2013-06-06
Hi Fred, checked your links.

Unfortunately I just installed Lubuntu 12.10 Alternate, which isn't a live CD.
 I can still get into the Live Index, although even though I can select from F1 to F10, I am unable to actually select any option.

 I'm tired after another day at this problem, but perhaps I'll install a live CD tomorrow and try again.

---

### Post by Gazucha on 2013-06-08
Why did I not see this before?

[http://www.toughbooktalk.com/public_downloads/HDD%20%26%20CDD%20swap/CF-28%20CD%20to%20DVD%20Swap.htm](http://www.toughbooktalk.com/public_downloads/HDD%20%26%20CDD%20swap/CF-28%20CD%20to%20DVD%20Swap.htm)

Apparently if you try to install an non-factory CD or DVD module, then the Toughbook won't boot!!!!!!!

 Need to solder across 2 points, et voila! (apparently)

Will try in the morning and let you know. It would certainly explain how it refuses to boot.

---

### Post by Gazucha on 2013-06-09
Hi again,

latest....

Ran a Lubuntu 12.10 Memtest and received a half million-plus # errors and although I had run Memtest on various other systems had never had any errors.

So, re-installed Mint 11 LXDE and spent all day running Memtest - without any errors!? So tried OldFred's boot solutions. 

Pressing shift twice during Boot does nothing.
From the Live CD, have no F1 to F6 to F10 options, but if I press esc from the CD menu I receive a DOS screen with the word, Boot: .... where I can write commands.

My question is how do I tell the system to boot from the Command Prompt?

---

### Post by Gazucha on 2013-06-10
Typed in, ~ $ startx

received lots but at the end...

Fatal server error:
no screens found

please consult the X.Org Foundation Support at [http://wiki.x.org](http://wiki.x.org) for help.

So what does that mean? The graphics drivers or essential components didn't load during install?

---

### Post by Gazucha on 2013-06-10
tried the workaround posted here...

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 but get, error cannot stat 'aufs' when I try to update grub.

---

### Post by oldfred on 2013-06-10
Are you at a grub command prompt or a system command prompt after you have logged in via terminal?

Have you tried recovery mode?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by mohanzeal on 2013-06-10
it may be the problem of the grub try installing the  grub this article may help you for [adding bootloader to ubuntu]("http://forzeal.com/ubuntu-boot-loader-not-showing-after-window-installation-solved/") , cheers if your problem is solved

---

### Post by Gazucha on 2013-06-10
Hi Fred,

 Not sure what the difference is re: Command Prompts and have been in at various points but right now, today, I am booting from a Linux Mint 11 LXDE DVD and then once on the main page am clicking "Ctrl + Alt + T". Then using 'that' window.

 Tried recovery mode in Lubuntu (if I remember correct) and it just stalled. 

As I have to pop out now for a while, I'll give the recovery mode a spin in this install and see what happens.

We must be able to crack this, as I have been running direct from the Live CD, surfing online and downloading files without a hiccup. The little git just refuses to Boot!

Stop press.... This Live CD has no "Recovery Mode" - Has "Compatibility Mode" - is that the same kinda thing? 

Clicked it anyway... Lots of text flying up and down the screen... screen gone blank but 'pulsing'  without text... 

Ok Text back... lots of Ok's and a final, "Welcome to Linux Mint"

mint@mint ~ $ _


Everything seems ok to me...

 

Whilst out, I'm gonna grab a blank CD, burn Yanns Boot-Repair and post the report. 

 Thanks again fella, 
speak later.

---

### Post by oldfred on 2013-06-10
No, recovery mode would be a choice in the grub menu after an install. 
Then entire live mode installer can be a repair system.

mint@mint is just the terminal mode in the liveCD.

---

### Post by mips on 2013-06-10
Ever considered moving the hard drive to a different computer and doing the install on that and then moving it back to the other computer?

---

### Post by Gazucha on 2013-06-11
Ok, typed in these commands several times and got error messages, 

***sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update*** ****** ******
 
***sudo apt-get install -y boot-repair && boot-repair***

So burnt a Boot Repair CD (but maybe should have been a DVD?) and now it is stuck 
in the DVD drive, can't boot anywhere and have that floopin flashing white 
line blinking away in the upper left hand corner.

erm.... ???

Is there any magic keyboard eject command?

Will try to do the install on another machine.

---

### Post by mips on 2013-06-11
> **Gazucha said:**
> 
Is there any magic keyboard eject command?

I doubt it but there's usually a small hole on the cd drive 'door' which allows you to insert a pin type object and open the drive that way.

---

### Post by Gazucha on 2013-06-11
> **mips said:**
> I doubt it but there's usually a small hole on the cd drive 'door' which allows you to insert a pin type object and open the drive that way.

Not this time, it's a Macbook Superdrive DVD-R that I added recently - It's OK, I'll just open it up and get the Disk out.

---

### Post by Gazucha on 2013-06-12
Opened the drive and retrieved the CD... burnt another Boot-repair 32bit.iso but when I boot the Toughbook, it just spits the CD out and returns to the blinking white line in the upper corner.

 Why does it boot from Linux iso's and not the Boot-repair ones?

 What am I missing?

---

### Post by oldfred on 2013-06-12
Which Boot-Repair ISO are you using? The full secureRemix is for newer computers.
The lightweight one may work if if a very old computer you may be into PAE issues. Only 12.04 of Lubuntu (and Xubuntu) have non-PAE kernels.

 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

      
 [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by Gazucha on 2013-06-12
Hi Fred,

 ok, will reinstall Lubuntu 12.04 and run boot-repair.

 Speak later.

---

### Post by Gazucha on 2013-06-12
Are there any keyboard shortcuts....

> **mips said:**
> I doubt it but there's usually a small hole on the cd drive 'door' which allows you to insert a pin type object and open the drive that way.

Found a keyboard eject trick....

 Press 'ENTER' as you shutdown or start-up...   Marvelous!



p.s. --- Spoke too soon..... Stuck again, 

Another day, no solution... Another 8 hours wasted....

---

### Post by Gazucha on 2013-06-13
So, reinstalled Lubuntu.

 When I press SHIFT on boot, I get the words, 'GRUB loading'. 

 Thats all folks! 

How do I run Boot-repair?

 Gonna try from the CD again...

---

### Post by Gazucha on 2013-06-13
Off to bed... CD is stuck again... 

 Cannot find Boot-Repair...

 Now have a,    [COLOR=#0000ff]boot: _[/COLOR]         in the upper left corner.

 What command could/should I enter?

 I'm tired.

 Good night.

---

### Post by oldfred on 2013-06-13
IF it is grub your get grub> or grub rescue. If a video driver you may get a blank screen or flashing underscore. 
Is the boot:_ from BIOS? And it is not seeing a bootable device?

---

### Post by Gazucha on 2013-06-13
Hola Fred,

 just wrote a long mail and it got deleted by mistake, so I'll try again...

[COLOR=#0000ff]Boot: _[/COLOR] appeared last night whilst pressing various buttons upon startup and after the Panasonic logo, - not totally sure which buttons but it is surely possible to return there.

I would imagine that it's not seeing any bootable device. Next time it appears, which command could/should be typed in?

 

Here's food for thought.....

 Currently running Lubuntu "Rescue Mode" and just arrived at a page where it reads,

 " The installer could not find any partitions, so you will not be able to mount a root file system. 
This may be caused by the kernel failing to detect your hard disk drive or failing to read the partition 
table, or the disk may be unpartitioned. If you wish, you may investigate this from a shell in 
the installer environment."

No Partitions found
   <Go Back>

------------------------------------

Now 100%, there was an sda1 partition along with a sda5 (or 6?) Swap partition.

 How do I investigate from this 'shell' I just entered? 

 

My head hurts. :)

---

### Post by mips on 2013-06-13
sudo fdisk -l

---

### Post by oldfred on 2013-06-13
First is BIOS seeing hard drive? If BIOS does not see a drive then no system will boot.
Then the BIOS has to find a bootable system in the MBR (if BIOS not UEFI).
MBR will then find more boot code either Windows in Windows partition or if grub it has some code (core.img) in sectors just after MBR and grub menu in the Ubuntu partition.

---

### Post by Gazucha on 2013-06-16
Apologies for the delayed response..

Hi again Fred...

> **oldfred said:**
> First is BIOS seeing hard drive? If BIOS does not see a drive then no system will boot.
Then the BIOS has to find a bootable system in the MBR (if BIOS not UEFI).
MBR will then find more boot code either Windows in Windows partition or if grub it has some code (core.img) in sectors just after MBR and grub menu in the Ubuntu partition.

Bios sees the Hard Drive - without problem

 How can I tell if *"MBR has found more boot code either Windows in Windows partition or  if grub it has some code (core.img) in sectors just after MBR and grub  menu in the Ubuntu partition."* ?

 Cheers

---

### Post by Gazucha on 2013-06-16
Hola Mips.

> **mips said:**
> sudo fdisk -l

[COLOR=#0000cd]fdisk -l [/COLOR]gives me a list of the Partitions...

/dev/sda1   *              2048     57573375     28785664   83   Linux  
/dev/sda2          57575422      58603519         514049    5    Extended
/dev/sda5          57575424      58603519         514049   82   Linux Swap / Solaris

With the asterix on sda1 indicating the Boot Partition.

Then what? 

Why is there the sda2 and why is it in the Swap space?

(p.s. no sudo needed)

---

### Post by oldfred on 2013-06-16
Grub does not use boot flag, but a few BIOS have to see a boot flag to even let you start to boot, so we still suggest you have one. It is required for the Windows partition with boot files.

With MBR partitioning you can only have 4 primary partitions. Windows has to be in a primary but Linux does not. To have more than 4 partitions you can convert any one primary to an extended partition. The extended partition is just a container for logical partitions and you can have many logical partitions in the extended. You only have swap in your extended.

BootInfo report shows details of what is in the MBR, PBR (usually just for Windows) and how grub is installed.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ronniew on 2013-06-16
has anyone suggested using PLop to boot from usb?

---

### Post by Gazucha on 2013-06-16
> **oldfred said:**
> 
BootInfo report shows details of what is in the MBR, PBR (usually just for Windows) and how grub is installed.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


This is where I was getting stuck before, as wasn't totally sure how and when to Boot the Boot-repair CD. Gonna try again.....

---

### Post by Gazucha on 2013-06-17
Aaha!

Boot-Repair* DVD*!

First run link is [http://paste.ubuntu.com/5773899/](http://paste.ubuntu.com/5773899/)

still not booting...

Running another now.

---

### Post by Gazucha on 2013-06-17
This is when I select the lower option box (ask for online support etc.) ~~~ [http://paste.ubuntu.com/5774120/](http://paste.ubuntu.com/5774120/)


Then ran this one with the "*repair file system*" selected.  ~~~ [http://paste.ubuntu.com/5774129/](http://paste.ubuntu.com/5774129/)

 Still only the flashing white line.....

---

### Post by Gazucha on 2013-06-17
> **ronniew said:**
> has anyone suggested using PLop to boot from usb?

Hi Ronniew, thanks for your reply,

 Yeah, it was suggested, back when I still had no optical drive.

How do you think that could help?
Bear in mind that the on-board USB is version 1.0. I have a PCMCIA card for USB 2.0

---

### Post by oldfred on 2013-06-17
If you only have USB1, that is not bootable, not sure if plop would then let you boot or not.

It looks like you install is fine. But with only one system you do not normally get grub menu. IF you hold shift key from BIOS does then grub menu appear?

It may be a video issue or other boot parameter is required.
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Gazucha on 2013-06-17
> **oldfred said:**
> IF you hold shift key from BIOS does then grub menu appear?

When I hold SHIFT, the word **Grub** appears. If I keep holding, the words **Grub loading** appear but no list or indeed any OS Boot.

 Cheers Fred, Gonna check your links. 

Maybe it is video related?

 I just don't quite get why it can run all graphical interfaces from DVD, yet can't seem to acccess the Hard Disk from Boot?

---

### Post by oldfred on 2013-06-17
You should be getting a grub menu.

I have found that grub sees key strokes even without menu. Try one down arrow after BIOS. It needs to be after BIOS but before menu would or should appear so you may need to try several times.
One down should give you the recovery mode boot option which has nomodeset and then should present other repair options?

Also if it has started to boot, do not force shutdown.

 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by Gazucha on 2013-06-17
Ok, the "**Reboot System Even If Ultimately Broken**" doesn't work, so I just Ctrl + Alt + Del to reboot... (the SysRq key is shared with PrtSc... Maybe this is why?)

 Pressing the **Down Arrow** doesn't change things either but I can enter the Recovery Mode Boot Options via the Lubuntu DVD. 

 From there, via F6, we have various options such as, **nomodest, noapic, acpi=off** and such like. 
I did try selecting '**nomodeset**' and then '**Boot from first Hard Disk**' in the menu but it just stalled ....

 Could I have damaged the OS by forcing shutdown? Should we maybe re-install again?

---

### Post by oldfred on 2013-06-17
Sometimes if system is in the middle of writing something, then system may have problems. Often caused by power failures. Then fsck will usually repair it.

I think booting from liveCD but even with nomodeset does not carry the nomodeset over to boot from first drive. It will then use settings on drive not from liveCD.

You can reinstall as that does not take long.  I prefer smaller / (root) of 10 to 25GB and the rest for /home or data partitions. That will not help your issues though.

---

### Post by Gazucha on 2013-06-17
Hi again, keep losing my Posts as I write, so now will keep it short...

 Sorry fella, what was your suggestion? fsck? Or reinstall? Any preferred OS for install? (had been Lubuntu 12.04 and Mint 11 LXDE)

Does Boot-Repair really fix the Windows MBR? ...Do you know?

 Cheers.

---

### Post by oldfred on 2013-06-17
Yes Boot-Repair can install a Windows compatible boot loader to directly boot Windows.

I do not think you need fsck. If you want to try a reinstall you can. Pick a version. I know Ubuntu.

---

### Post by Gazucha on 2013-06-17
> **oldfred said:**
> Pick a version. I know Ubuntu.

I imagined that Lubuntu 12.04 would be good but maybe I should look at an older release? 


 Have to pop out for a bit but will check when back.

Gonna try both Linux and Windows re-installs today and see what happens.

 Thanks again Fred for your time and patience.

 Laters.

---

### Post by Gazucha on 2013-06-17
Re-installed both Win XP Pro and Lubuntu 12.04 and still have the flashing little white line in the upper corner.

What is the problem? The graphic card works fine from optical media and it connects online without a glitch...

 Why won't it Boot from the Hard Disk?

 Are Toughbooks fire-resistant? 

I'm not far off from administering that test!!!!

 Gonna try installing Win2000

---

### Post by oldfred on 2013-06-17
I think it was someone else with an older toughbook that had issues. Not sure they resolved them.

[http://ubuntuforums.org/showthread.php?t=1496711](http://ubuntuforums.org/showthread.php?t=1496711)
Used this parameter:

i915.modeset=1

---

### Post by Gazucha on 2013-06-18
Win2000 reinstall ---         flashing white line
Lubuntu 12.04 reinstall  -- flashing white line..

---

### Post by Gazucha on 2013-06-18
> **oldfred said:**
> I think it was someone else with an older toughbook that had issues. Not sure they resolved them.

[http://ubuntuforums.org/showthread.php?t=1496711](http://ubuntuforums.org/showthread.php?t=1496711)
Used this parameter:

i915.modeset=1


Looks interesting. According to the thread this resolved their problem. 
 I think I still have an old Ubuntu 10.10 or else will try to download a 9.10. 

 Cheers Fred. Let's give it a go.

---

### Post by Gazucha on 2013-06-18
Ok, changed the HD from 160Gb to 40Gb.

 installed Ubuntu 9.10, changed the code to add **[COLOR=#0000cd]i915.modeset=1[/COLOR]** and...

 we have progress!

 Not a lot, but it booted up to the words;

[COLOR=#0000cd]** Grub loading.**[/COLOR]
  **[COLOR=#0000cd]_[/COLOR]**

(with the flashing white cursor beneath)

 Before, I had to hold SHIFT to get that.




*Next*............... Lol!

P.s. These CF-28's only read Hard Disks up to 128Gb so thought that may be a problem.

---

### Post by Gazucha on 2013-06-18
I'm wondering...

 My "raising Skinny Elephants etc" command isn't working at all....

 According to this person found here, RE: Raising Skinny Elephants....

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Nikpe890                                                                                [ synterr55]("http://kember.net/articles/reisub-the-gentle-linux-restart/#comment-179623023")                                                   &#8226;                                                       [2 years ago]("http://kember.net/articles/reisub-the-gentle-linux-restart/#comment-205441090")                                                   
[COLOR=#0000cd]"If it doesnt work, your kernel has crashed"[/COLOR]

So,*** HAS*** my Kernel crashed? If so, into what? And where do I find a reliable Kernel mechanic? Could it not be a Bios problem? There is some funny stuff in there..
 
These questions - and more - shall be answered in the next thrilling installment of CF-28's "XXXX Filesystem!!" 

 Stay tuned...   ):P

---

### Post by oldfred on 2013-06-18
google has some info, for example.

[http://forum.notebookreview.com/panasonic/369483-cf-28-touch-screen-installation-recent-linux-distributions.html](http://forum.notebookreview.com/panasonic/369483-cf-28-touch-screen-installation-recent-linux-distributions.html)

---

### Post by Gazucha on 2013-06-18
Edit to remove....

---

### Post by Gazucha on 2013-06-18
> **oldfred said:**
> google has some info, for example.

[http://forum.notebookreview.com/panasonic/369483-cf-28-touch-screen-installation-recent-linux-distributions.html](http://forum.notebookreview.com/panasonic/369483-cf-28-touch-screen-installation-recent-linux-distributions.html)

 Hola Fred,

 I actually encountered this page before but it seemed a mind boggling at the time.

 I'll have a good look if I can tomorrow (busy day) and report back.

 Thanks again eh?

---

### Post by schuck on 2013-06-26
Ummm,this may be a dumb question,but seeing the toughbooks age,have U looked in the sytem bios to make sure it's set to recognise non-dos OS's? (OS type MS-DOS,or OTHER) I had a tower that wouldn't boot a ubuntu HDD unless it was set to other.It was a P3 processor system.Also recomend trying a copy of ubuntu 8.04 if possible.probably more compatible with the hardware involved. good luck.

---

### Post by Gazucha on 2013-06-26
Don't see an option in the bios to recognise non-Dos OS's.

I'll try 8.04 and let you know...

 Woke up today deciding to just sell it to a tec (with time) or for parts.

 Lets see.

I honestly am getting bored and have given weeks of my life to resolving this.

---

### Post by Gazucha on 2013-06-26
I did wonder if it wasn't a Bios problem but seeing as you need an OS to upgrade the Bios, that makes the CF28 a brick... Without a second CF28 to swap drives.

---

### Post by Gazucha on 2013-06-26
Ok... 8.04 is not installing.

Just gives me Dos script after the Ubuntu Install Menu!

 Anyone wanna buy a CF28?

 Trying now to Boot in Safe Mode

1st line says..

[COLOR=#0000cd]ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 Frozen[/COLOR]

 Keeps repaeting stuff like that, with the occasional 

[COLOR=#0000cd]SQUASHFS error [/COLOR]

and 

[COLOR=#0000cd] BUFFER I/O error on device sr0[/COLOR]

and 
[COLOR=#0000cd]
unable to read page, block74dd2f size 2ab9[/COLOR]

 Does that mean knacked HD?

---

### Post by Gazucha on 2013-06-26
Here's something different... The screen went all wierd and no keys would work. Back to normal after reboot.

Please check the attached photos.

That happened after leaving Ubuntu 8.04 installing for about 6 hours. 

It has never done that before.

 Any ideas?

---

### Post by oldfred on 2013-06-26
No idea? But 8.04?

---

### Post by Gazucha on 2013-06-27
Hi Fred,
Yeah I know, 

8.04 was just a test that someone on the the Toughbook Forums suggested (being a Pentium III 800Mhz laptop and all that...).

Didn't even come close to installing anyway - unlike Mint 11 LXDE and Lubuntu 12.04 and even Windows.

Gonna check today for hardware info on the CF28 graphics (or video) card/board/chip, as I disassembled it last week in the hunt for any bad connections and perhaps mis-connected something upon reassembly?

 I've put it up for sale anyway.....

---

### Post by Gazucha on 2013-07-10
I HATE admitting defeat... but this one beat me.


The problematic CF-28 is sold!!!

Thankyou Fred, thankyou all who contributed and I am sorry we cannot offer a solution to future readers.

Adios, hasta la huego.


Thread closed...........

---

