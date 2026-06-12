---
title: "Computer only sees one hard disk"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Odyssey1942 on 2007-01-28
During a recent enforced stay at home, I installed 6.10 on a new drive and took it to the office to replace the current drive of one of the computers there. I say replace though it is more like  a "weaning off of the old drive onto the new one".

I replaced the old drive with the new one as the master (as far as the cable connectors go), but it wouldn't boot, so I just installed 6.10 again which only took a few minutes. Perhaps unfortunately I did so without plugging the old drive in again (on the slave connector), so now when I want to choose which drive I want to boot from, the computer just automatically boots from the drive that has the "master" cable connector (both drives set to cable select and both are on the same cable).

I would like grub to give me a choice between the two. What do I need to do to make it see both at boot?

---

### Post by dbbolton on 2007-01-28
that sounds more like a bios problem to me.

---

### Post by Odyssey1942 on 2007-01-28
By bios problem, do you mean mis-configured? If so, how does that impact on the boot loader and how should it be configed?

---

### Post by dbbolton on 2007-01-28
i don't have any experience with multiple hard drives. however, bios must have a specific boot order, such as- 1. CD-ROM 2. Hard Disk 3. USB Drive- or what have you. bios tries to boot from #1 first, and if there is nothing there to boot, it tries #2 and so on. it would seem to me that two different hard disks would have to be two separate entries in the boot order.

---

### Post by ieee488 on 2007-01-28
Doesn't sound like a BIOS problem to me.

It sounds like with the install Ubuntu did not install GRUB. I don't know if it does that automatically even if Ubuntu was the only OS or not.

If you don't have GRUB, someone mentioned using Super Grub to restore it.

And then you probably have to edit /etc/menu.lst to add entry for your old drive.

---

### Post by logos34 on 2007-01-28
I think it's just a matter of editing grub config files...Grub doesn't know the other drive/os exists because it wasn't connected during install...in cases like this you simply need to add it to /boot/grub/menu.lst and /etc/fstab files (to automount)...

Post the output from
sudo fdisk -l

and your menu.lst too.

You have another version of Ubuntu on the old drive?

and do you see grub at (even fleetingly) during boot?

---

### Post by Odyssey1942 on 2007-01-29
I can only see grub by pressing <esc> (if I remember correctly) during the boot up, but it only shows the one drive.

The "old" drive is Ubuntu 5.04 and the new one is 6.10.

When I get to the office, will post fdisk and menu.lst. 

I am inexperienced at editing files such as menu.lst, but will appreciate all guidance.

Will google/read on Super Grub.

thanks to all

---

### Post by ieee488 on 2007-01-29
Then it sounds like you do have Grub, but since there is only one OS on that one hard drive, it automatically boots into Ubuntu 6.10.

You'll have to search around for posts about adding a second hard drive to /etc/menu.lst
I've only had experience with commenting things out. And you might have to edit /etc/fstab as well.

This is just me, but I'd do the re-install of 6.10 on the new drive with the old drive attached.

---

### Post by Odyssey1942 on 2007-01-29
The re-install will certainly be the most expedient remedy, but if I do I will only have learned that all devices to be installed by grub (i.e., listed as a choice during bootup) need to be in place at the time of Ubuntu installation.

Before that approach (as my safety net) will have a go at editing the files mentioned and see what happens. Thanks.

---

### Post by ieee488 on 2007-01-29
Please let us know how it works out.
I am very interested in learning what you had to do to make it work.

---

### Post by Odyssey1942 on 2007-01-29
I didn't have much time to get under the hood, so I tried just replacing the cd-rom with the new drive on the second ide channel and re-booting, but the boot loader didn't see the new drive. Does make one question whether the bios also didn't see it. Can't imagine why that might be though?

Will have to get the file editor out tomorrow.

---

### Post by ieee488 on 2007-01-29
The bootloader isn't going to see it just by the mere fact of you plugging in the drive. You're going to have to fire up the text file editor.

---

### Post by Odyssey1942 on 2007-01-30
The text editor is open and the learning is happening.

I think that I had read somewhere that grub took a handoff of hardware info from bios during the boot process, but that probably only applies to situations where the "install" has already occured with the hardware in place (or text files appropriately modified). In other words, grub will know when something that it is looking for is not fed to it by the bios, but can't assimilate new hardware info from bios.

Would this be correct? If not, any clarification will be appreciated.

---

### Post by ieee488 on 2007-01-30
I'm not an expert on this by any means. 
I only know that when I went about deleting a partition using GParted, I not only had to edit /etc/menu.lst but also  /etc/fstab

I don't believe that GRUB is communication with the BIOS. As far as I know, GRUB is looking at /etc/menu.lst 
GRUB happens much later in the boot up process.

Below is my /etc/menu.lst


```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb6 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb2.
title		SUSE Linux 10.1 (on /dev/hdb2)
root		(hd1,1)
kernel		/boot/vmlinuz root=/dev/hdb2 vga=0x31a resume=/dev/hdb5 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb2.
title		Failsafe -- SUSE Linux 10.1 (on /dev/hdb2)
root		(hd1,1)
kernel		/boot/vmlinuz root=/dev/hdb2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by Odyssey1942 on 2007-02-01
OK, got it sorted and am posting this for anyone who is interested or may in future face a similar situation.

Turns out that I had 2 hdd's, both jumpered to cable select and a CDRom, which was jumpered to master (as it was the master on ide2). Who would have thought it, but this kept Ubuntu from seeing the second hdd, no matter which one I booted from (by disconnecting the other one). Apparently when any ide device is set to CS, they all must be. So the CDRom is now also CS, and now Ubuntu can see both hdd's (fdisk -l)

Then it was a matter of mounting the second hdd and editing fstab and menu.lst for that drive. It now gives a choice of hdds to boot from at grub. Yes!

Thanks to all who helped.

---

