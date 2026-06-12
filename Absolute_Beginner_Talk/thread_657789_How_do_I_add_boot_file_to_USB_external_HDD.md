---
title: "How do I add boot file to USB external HDD"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by kent41 on 2008-01-03
HI
I currently DO NOT have any Hard drive in my ACER Laptop.
I am using a live 6.1 CD. 

I have installed Ubuntu 6.10  using the Live CD to an external USB HDD (Not a USB thumb drive)  This is a 60 gig Hitaci Hard drive.

I can use the live CD to access the the USB HDD and look at files ok.

The problem is the USB external HDD will not boot. I get a message it can not find the boot file.  I was under the impression the install would create the boot file,

I have changed the BIOS to boot from USB HDD and USB FDD but neither will boot.

My question is there a way to write a boot file to the USB HDD ?

EDIT  Using gparted I see the boot flag is set.

Thanks
 Kent41

---

### Post by gurrett86 on 2008-01-04
When you install grub you need to make sure it installs to your external...do a fdisk -l command to see what the drive number is. Look on the forums for installing grub...they should be of use. Sorry if I wasn't much help. :(

---

### Post by kent41 on 2008-01-04
bump

---

### Post by Dedoimedo on 2008-01-04
Hello,

Do run the following commands and tell us what you see:

sudo fdisk -l

sudo gedit /boot/grub/menu.lst

Cheers,
Dedoimedo

---

### Post by kent41 on 2008-01-04
> **Dedoimedo said:**
> Hello,

Do run the following commands and tell us what you see:

sudo fdisk -l

sudo gedit /boot/grub/menu.lst

Cheers,
Dedoimedo

Hi dedoimedo

this is what the data looks like.
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6996    56195338+  83  Linux
/dev/sda2            6997        7296     2409750    5  Extended
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris
```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=9bac860d-3e37-4c6d-8556-646a31dc0ae8 ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST




```

---

### Post by kent41 on 2008-01-04
bump

---

### Post by kent41 on 2008-01-04
**UPDATE:**

I changed the **hd0,0** reference in /boot/grub/menu.lst  to **sda0,0**

and now when I try to boot from the external USB HDD the screen displays "**GRUB _** "and stops.

Does anyone have any ideas what I can do to boot the USB HDD ?

Thanks Kent41

---

### Post by logos34 on 2008-01-04
> **kent41 said:**
> **UPDATE:**

I changed the **hd0,0** reference in /boot/grub/menu.lst  to **sda0,0**


(hd0,0) is the correct format.

Have you tried to reinstall grub bootloader to the MBR?
(from live cd):

sudo grub

grub> find /boot/grub/stage1
(should show 'hd0,0'.  Enter output on next line)
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

ADD: also, comment out 'hiddenmenu' option in menu.lst:
> 
[COLOR="Red"]#[/COLOR]hiddenmenu

---

### Post by kent41 on 2008-01-04
> **logos34 said:**
> (hd0,0) is the correct format.

Have you tried to reinstall grub bootloader to the MBR?
(from live cd):

sudo grub

grub> find /boot/grub/stage1
(should show 'hd0,0'.  Enter output on next line)
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

ADD: also, comment out 'hiddenmenu' option in menu.lst:

Thanks for the reply logos34

I used the following commands to mount mount the external USB HDD.

```

kent@kent-laptop:~$ sudo mkdir /media/usb
kent@kent-laptop:~$ sudo mount /dev/sda1 /media/usb

```

I then did  CD /media/usb  to make changes to /boot/grub/menu.lst file.

Yes I changed the sda0,0  back to  hd0,0 
I then entered all your suggested commands and got the same results that you did.

I also commented out the hiddenmenu.

Then I re-booted the external HDD but I got the GRUB message and could not get the GRUB menu when I pushed the <ESC> button.

---

### Post by logos34 on 2008-01-04
it there a 'stage2' file in /boot/grub? 

what about trying the 'boot from first hard disk' option on the live CD menu screen?

---

### Post by logos34 on 2008-01-04
read through the suggestions [here]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_").

try Super Grub Disk

---

### Post by kent41 on 2008-01-04
> **logos34 said:**
> it there a 'stage2' file in /boot/grub? 

what about trying the 'boot from first hard disk' option on the live CD menu screen?

Yes there is a stage2 file in /boot/grub on the external HDD.

When I tried to boot from the first hard drive option on the cd I got a failure that said something about local drive failure.

---

### Post by logos34 on 2008-01-04
hmm...well read post #11 above, maybe check the hard disk settings in the Bios.

Try installing Feisty or Gutsy.

---

