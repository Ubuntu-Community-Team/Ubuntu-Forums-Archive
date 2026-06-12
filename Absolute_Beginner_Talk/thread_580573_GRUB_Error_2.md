---
title: "GRUB Error 2"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-18
I just did a fresh installation of 7.10 and now I get a grub error 2.  Is there any way to fix this? I need to get onto windows tonight

---

### Post by Dapman01 on 2007-10-19
bump, come on guys there has got to be something I can do

---

### Post by logos34 on 2007-10-19
open a terminal from the livecd and run this:
[B]
sudo fdisk -l[/B]

post it

---

### Post by Dapman01 on 2007-10-19
Sorry, I am installing feisty just so I can try to get to my windows files.  I'll reinstall Gusty later tonight to try to get it to work.  I tryed to reinstall it twice and it gave me the same error.  
Thanks for responding and I'll come back on when I install gutsy again...an if I have that error

---

### Post by Dapman01 on 2007-10-19
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38156   306488038+  83  Linux
/dev/sdb2           38157       38913     6080602+   5  Extended
/dev/sdb5           38157       38913     6080571   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

that's what I got

---

### Post by logos34 on 2007-10-19
Reboot to the grub menu screen and hit 'e' key on the highlighted gutsy kernel.  Hit 'e' key again on the 'root' line and change from '(hd0,0)' to '(hd**1**,0)' or vice-versa.

---

### Post by Dapman01 on 2007-10-19
It doensn't give me a chance to type anything in

GRUB loading stage1.5


GRUB loading, please wait...
Error 2
_ (this blinks but doesn't let me type anything in)

---

### Post by logos34 on 2007-10-19
Boot the livecd and mount your root partition, sdb1.  Go to /boot/grub/menu.lst.  Post it.

---

### Post by lordpuppet on 2007-10-19
something like that happened to me once. I fixed it by selecting the "format" option on the partition where i was installing ubuntu during the installation (the one with the " / " ).

---

### Post by Dapman01 on 2007-10-19
> **logos34 said:**
> Boot the livecd and mount your root partition, sdb1.  Go to /boot/grub/menu.lst.  Post it.

Could you clarify that a little please.
What do I need to put in the terminal

---

### Post by Dapman01 on 2007-10-19
ok, right after that post I got what you said


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
# kopt=root=UUID=51cc7d45-8ff9-479e-bbe4-d3099da1512a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51cc7d45-8ff9-479e-bbe4-d3099da1512a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51cc7d45-8ff9-479e-bbe4-d3099da1512a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2007-10-19
edit: we posted together

---

### Post by logos34 on 2007-10-19
try reinstalling grub:

> sudo grub
root (hd1,0)
setup (hd0)
quit

---

### Post by Dapman01 on 2007-10-19
That didn't work
I think that i failed to mention that this is on an external drive.
Is there anyway to bypass GRUB and disconnect my hard drive so I can get to windows

---

### Post by logos34 on 2007-10-19
> **Dapman01 said:**
> That didn't work
I think that i failed to mention that this is on an external drive.
Is there anyway to bypass GRUB and disconnect my hard drive so I can get to windows

oh, then in that case maybe the problem is that your Bios does not support booting from USB. 

If you have the windows install CD you can restore the NTLDR (bootloader) by entering the recovery console and doing **fixmbr** command.  Or if you have a DOS boot floppy you can do fdisk /mbr.

Otherwise try the [Super GRub Disk CD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

---

### Post by Dapman01 on 2007-10-19
Thank you so much for your help, I appreciate it.
I had to go to bed last night and I am in class right now, but I downloaded the suber grub disk 
Do I use it just like a boot disk?

---

### Post by logos34 on 2007-10-19
> **Dapman01 said:**
> Do I use it just like a boot disk?

yep.

---

### Post by Duck2006 on 2007-10-19
> **Dapman01 said:**
> Thank you so much for your help, I appreciate it.
I had to go to bed last night and I am in class right now, but I downloaded the suber grub disk 
Do I use it just like a boot disk?

Yes.

---

### Post by Dapman01 on 2007-10-19
ok, so I got windows to load through the super grub disk, but I can't get ubuntu 7.10 to work.  I wonder if it doesn't support 7.10 I tried fixing the boot but it says it fails

---

### Post by zvadinov on 2007-10-19
Hello together

I have exact the same Problem, only without Windows and it isn't a externel drive. After the Installation
of Gutsy Gibbon I recive at boottime the "Error 2" -Code  cant do anything ! :-(((

can anyone help ?

zvadi

---

