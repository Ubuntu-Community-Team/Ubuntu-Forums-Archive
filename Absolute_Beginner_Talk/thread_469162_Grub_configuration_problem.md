---
title: "Grub configuration problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by imog on 2007-06-09
EDIT:  This has been fixed, details of the problem and the resolution are below.

I have a T43 running XP.  I loaded Feisty 7.04, choosing to resize the windows partition and use free space.  This went fine.

I rebooted into Feisty (Grub came up with OS options and I selected Ubuntu) and I proceeded to run all available updates.  I then rebooted and loaded back into Feisty (I wasnt paying attention and Grub defaulted to Feisty) and it loaded fine.  I then rebooted into XP and it loaded fine, running the checkdisc due to the partition resize.  I then rebooted back into XP and it detected new devices (presumably the new Linux partitions) and prompted for reboot, so I rebooted once more.  This went bad.

After this final reboot, I POST, the initial black screen comes up stating "Grub loading stage1.5."  Thats the normal message Grub displays right before listing the OS options to boot, however immediately after that message I do not get the list of OS options.  Instead, it immediately goes into a soft reboot which drops me back to the POST screen, displays "Grub loading stage1.5", wash, rinse, repeat.

So I'm stuck in a reboot loop right before I get the list of OS's to load.  Clearly a Grub problem.  I need a hand holding on fixing Grub - I've never configured or had to even touch it before.  I will look up how to find my current Grub config (whatever might be useful for you kind folks who will be around to help me), and I will post it here ASAP.

---

### Post by imog on 2007-06-09
I will do the following next, from [this thread](http://ubuntuforums.org/showthread.php?t=426161&highlight=grub+loading+stage1.5):

[quote=undecidable]You need to check that grub is trying to boot to the correct partition.

If you can boot to the Feisty live CD,
compare /boot/grub/menu.lst 
to fdisk -l
and ensure they are pointing to the same thing. 

Also check that menu.lst does not have an entry that is pointing to itself
(the entry to boot to windows is a 'chainloader' entry,
which if incorrect can point back to grub itself)

You can also check that grub can find the system.
Normally you can get into the grub comman line from the grub menu
but as you ar not getting to the grub menu, you will have to do it from a live CD.
sudo grub
wil take you to a grub prompt, then:
find /vmlinuz
to ensure grubv is finding your linux kernel where it expects to.

Hope this helps.[/quote]

---

### Post by imog on 2007-06-09
This is my menu.lst:

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
# kopt=root=UUID=0fcfb6e9-a4db-42fb-be43-a58200c6113d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0fcfb6e9-a4db-42fb-be43-a58200c6113d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0fcfb6e9-a4db-42fb-be43-a58200c6113d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0fcfb6e9-a4db-42fb-be43-a58200c6113d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0fcfb6e9-a4db-42fb-be43-a58200c6113d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
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
```

This is the output of fdisk -l:
```
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3616    29045488+   7  HPFS/NTFS
/dev/sda2            3617        4805     9550642+  83  Linux
/dev/sda3            4806        4864      473917+   5  Extended
/dev/sda5            4806        4864      473886   82  Linux swap / Solaris
ubuntu@ubuntu:/$ 

```

It appears that grub is looking in the right place for the linux kernel:
```
grub> find /vmlinuz
 (hd0,1)

grub>
```

I'm going to look at this, and see if anything jumps out at me but I really don't know what I'm looking for - any input is appreciated.

---

### Post by imog on 2007-06-09
Ok, so I fixed Grub.

I booted to the LiveCD and issued "grub" at the terminal prompt.  At the Grub prompt I typed "root (hd0,1)" then hit enter.  I then typed "setup (hd0)" then quit to exit grub prompt and rebooted the system.

Upon reboot, the Grub OS menu displayed.  I booted back into Feisty without issue.  I rebooted back into XP without issue.  So the Grub problem was fixed.

Then I figured out that running XP breaks my Grub install, and puts me right back where this thread started.  I'm going to start another thread specific to discussing how to keep this problem from returning.  Hope this thread may help someone in the future.  Feel free to post if you have any questions about what I did to resolve this problem.

---

