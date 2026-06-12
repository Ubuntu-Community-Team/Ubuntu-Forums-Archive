---
title: "installed ubuntu after winXP, ubuntu OK, but winXP cannot start"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by McWilliamsPete on 2008-01-05
have disk with 7 partitions, winXP uses 6 of them, 7th was reserved for ubuntu.
now have installed ubuntu (from German magazine c't special Linus Ubuntu 7.10).
ubuntu works OK, but winXP cannot start. boot manager gives error that Windows
could not be started, since following file missing or damaged:
  <Windows root>/system32/hal.dll

anyone have that experience?

thanks,
Pete

---

### Post by nick_h on 2008-01-05
What is the contents of your /boot/grub/menu.lst file?

---

### Post by tylerspaska on 2008-01-05
i would try to download the hal.dll and place it in the system32 folder. also see if there already is one there when you boot in ubuntu - you should still have access to your XP filessystem right?

[http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)

if there is already one there i would make a backup of that dll before trying to replace it with one downloaded from the net.

---

### Post by McWilliamsPete on 2008-01-06
here is my menu.lst file attached.
I just noticed: I installed winXP to D:, not to C:.  this just might be the problem...

thanks,
pete

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=5b857792-2f8a-43e7-b7a7-0831f9e334cf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b857792-2f8a-43e7-b7a7-0831f9e334cf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b857792-2f8a-43e7-b7a7-0831f9e334cf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

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

---

### Post by McWilliamsPete on 2008-01-06
I just noticed: I installed winXP to D:, not to C:. this just might be the problem...

how could I get this into the boot manager?

---

### Post by nick_h on 2008-01-06
OK. The D: drive will be (hd0,1) rather than (hd0,0) so you will need to change the root device.

Have a look in the [Grub manual](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows) for details.

---

### Post by McWilliamsPete on 2008-01-07
thanks for the tip.
if I edit the menu.lst file, is it being read by the boot manager, or where do I go for that?

pete

---

### Post by glennzo on 2008-01-07
Open /boot/grub/menu.lst in a text editor and change (hd0,0) to (hd1,0). If Windows still doesn't like that then you may need to add
map (hd0) (hd1)
map (hd1) (hd0)
Above chainloader +1

---

### Post by forestpixie on 2008-01-07
yep editing the menu.lst file will do what you want

---

### Post by caravel on 2008-01-07
If you installed XP to D: and not C:, the boot.ini and bootloader may still be in C:, so you need to be aware of this.

---

### Post by louieb on 2008-01-07
GRUB has a feature - you can  edit an entry on the fly.  
Highlight the XP entry and press **e**  
Highlight the line you want to change and press [B]e
[/B]Make  changes, then press **enter**
Press **b** to boot when done.

Changes are temporary. To make permanent change /boot/grub/menu.lst.
Nice way to test an entry without rebooting.

---

