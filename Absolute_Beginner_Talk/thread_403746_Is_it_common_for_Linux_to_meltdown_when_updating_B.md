---
title: "Is it common for Linux to meltdown when updating BIOS?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-04-07
I recently had to update my motherboard's BIOS to troubleshoot some hardware problems in Windows XP.
But when I later try to run my Ubuntu partition it seems like it has been broken for good.  Windows XP still boots fine ater BIOS update.
These are some of the ERROR messages I get when running "Ubuntu in Recovery mode" trough GRUB.

```
Security Framework v1.0.0 initialized
SELinux: Disabled at boot.
ACPI: Looking for DSDT...not found!

...MP-BIOS bug:8254 timer not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A...failed
...trying to set up timer as Virtual Wire IRQ...failed
...trying to set up timer as ExtINT IRQ...failed :(.

Kernel panic-not syncing: IO-APIC+timer doesn't work!

Boot with apic=debug and send a report.  Then try booting with the 'noapic' option
[17179569.908000]
```

Is there an easy solution for this or does every BIOS update mean total / (root) re-installation for Ubuntu?

---

### Post by dstew on 2007-04-07
Does it boot when you use the 'noapic' option? You could also add 'nolapic'. Did you try apic=debug as recommended? Maybe that will give a clue as to what to do.

I don't think you will need to install again. Your kernel was trying to use the interrupt controller and timer to speed up its boot process, but something in your new bios has changed how those circuits behave. I think the 'noapic' boot option only affects how fast the kernel loads, and has no effect on how your system works. Go ahead and try it.

---

### Post by jingo811 on 2007-04-08
Eh... I have used GUI GrubEDit to filter away all uneccessary Kernels from the booting GRUB list a long time ago.  So I can't see anything but the below options when booting.
--------------------------------------------
Ubuntu 6.06
Ubuntu 6.06 recovery mode
Windows XP
--------------------------------------------

How can I access that "noapic" option now?

---

### Post by bmt on 2007-04-08
> **jingo811 said:**
> How can I access that "noapic" option now?
You can edit the grub menu at boot time.  Instructions are on the screen, but in general terms (working from memory, so don't assume this is all correct!):

Press 'e' to edit the menu entry (the one that usually boots you into Linux, 'Ubuntu 6.06').  *Don't press 'Enter'!*

There will be a line near the top of the next screen starting with 'kernel ...', which has entries at the end of it somethng like 'splash' and 'quiet'.  Use the cursor keys to move to that line and press 'e' again to edit the line.

At the end of that line, add 'noapic' (without quotes).

Press 'b' to boot with that modified grub menu entry.

The modified entry is effective for one boot only -- no permanent changes are made.  (To make permanent changes, edit the /boot/grub/menu.lst file.)

---

### Post by jingo811 on 2007-04-08
Hey it worked the first try BMT :) tnx!
Now where do I send that bug report?
```
Boot with apic=debug and send a report.  Then try booting with the 'noapic' option
```

**PS.**
Add your comments at the Bug Report I made here if you have similar problems with your Motherboards:
[https://bugs.launchpad.net/ubuntu/+bug/104550](https://bugs.launchpad.net/ubuntu/+bug/104550)

---

### Post by jingo811 on 2007-04-10
Now my PCs bad curse is starting to kick in again :( Hardware stuff gets confused again which requires manual input everytime to fix it.

Anyhow what I want to do now is make my kernel start with "noapic" on every boot.  But somehow when I edit my menu.lst it erases the "noapic" fix after some days :confused: 
> bill@Wudoo:~$ **cd /boot/grub**
default        fat_stage1_5  menu.lst         menu.lst.GruBK     stage1
device.map     images        menu.lst~        minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5  menu.lst_backup  reiserfs_stage1_5  xfs_stage1_5
bill@Wudoo:/boot/grub$ **sudo gedit menu.lst**
Password:


My menu.lst and where I added "noapic" and saved the file.  Scroll all the way down to find my tampering!  Is this correctly done?  
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash [COLOR="Red"]noapic[/COLOR]**
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by dstew on 2007-04-10
That is the correct way to edit the menu.lst file.

One more thing you might check. Some BIOSes have an IO_APIC setting. If yours does, changing it might help.

---

### Post by mcduck on 2007-04-10
> **jingo811 said:**
> Now my PCs bad curse is starting to kick in again :( Hardware stuff gets confused again which requires manual input everytime to fix it.

Anyhow what I want to do now is make my kernel start with "noapic" on every boot.  But somehow when I edit my menu.lst it erases the "noapic" fix after some days :confused: 


My menu.lst and where I added "noapic" and saved the file.  Scroll all the way down to find my tampering!  Is this correctly done?  
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash [COLOR="Red"]noapic[/COLOR]**
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Youshould also add it to default options, otherwise it will disappear when next kernel update comes. When you get a kernel updates it reads default options and uses them to generate entry lines for the new kernel.

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=quiet splash [COLOR="Red"]noapic[/COLOR]**

---

### Post by jingo811 on 2007-04-12
tnx.
> 
One more thing you might check. Some BIOSes have an IO_APIC setting. If yours does, changing it might help.
Yeah I tried to disable everything on my BIOS that had anything with APIC to do, sometimes Ubuntu liked it.  Sometimes the errors are the same.
But Windows XP partition didn't like when I disabled any APIC stuff in BIOS so the menu.lst fix seems to be the most sanest chose for me.

---

### Post by Jonam on 2007-04-12
> **mcduck said:**
> Youshould also add it to default options, otherwise it will disappear when next kernel update comes. When you get a kernel updates it reads default options and uses them to generate entry lines for the new kernel.

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=quiet splash [COLOR="Red"]noapic[/COLOR]**

Another problem explained! My GRUB reverted to a very old version straight after I did the latest Kernel update today. I had to manually change menu.lst and also re-activate the swap space on the hard-disk using mkswap and swapon. I couldn't figure out why this happened until I read this post and on checking menu.lst found the default options were set to what I had when I first installed Ubuntu (two hard-drives). Still doesn't explain the loss of the swap space though.

Nice to know this though. I will be careful with the next kernel upgrade.

Jonam

---

