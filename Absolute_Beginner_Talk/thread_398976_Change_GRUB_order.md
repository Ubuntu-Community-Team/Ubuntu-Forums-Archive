---
title: "Change GRUB order"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by UR2CLOSE on 2007-04-01
I need to know the easiest way to change/edit the GRUB or is it bootloader at the start of my system which dual boots between Ubuntu Edgy 6.10 and Windows XP.  I have 3 harddrives and Ubuntu is loaded on the third drive hda2.  I am suffering from information overload trying different things to get it sorted out.  Thanks for your help, Steve:popcorn:

---

### Post by 3rr0r on 2007-04-01
What do you mean change the order?  Change the order in which it lists the OS's ?  I would most definately not do that, because if there is ever an update to your kernel it will have problems finding your latest due to the change in the order.  If you want to edit the time you have to choose an OS, or set it so that after the time expires it will choose one for you, let me know.

---

### Post by sad_iq on 2007-04-01
Try **sudo nano /boot/grub/menu.lst** 
 Also read about it here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
 but what are you trying to change there(to avoid all that "information overload")?

---

### Post by UR2CLOSE on 2007-04-01
My children need access to Windoze to use various things loaded there, Ubuntu is for me to use and learn for the moment.  I wanted Windoze to be the first choice to load because they do not always catch or understand the start options but if that causes a problem as 3rrOr pointed out I will have to train them a bit better.  

Do I need to keep all the past kernel start options in the GRUB? 

Thank you all for responding so quickly.

---

### Post by alien21010 on 2007-04-01
Nope you can just move the order of the items in your /boot/grub/menu.lst file, so take the Windows entry in its entirety and move it above the Ubuntu entry, and it will now become your default entry.  

Thats all you have to do.  Note:  You should make a backup copy or the menu before you edit it!  

If you need more help let me know.

---

### Post by confused57 on 2007-04-01
> **UR2CLOSE said:**
> My children need access to Windoze to use various things loaded there, Ubuntu is for me to use and learn for the moment.  I wanted Windoze to be the first choice to load because they do not always catch or understand the start options but if that causes a problem as 3rrOr pointed out I will have to train them a bit better.  

Do I need to keep all the past kernel start options in the GRUB? 

Thank you all for responding so quickly.
You can always move your Window's entry to just above the line:
###BEGIN AUTOMAGIC KERNELS LIST

it's how I have my entry set up, Window's will boot unless I select Ubuntu manually at the boot grub menu...in fact, you could just copy & paste it there & have both entries.  Kernel updates will not affect your booting order.

See the 3rd link in my signature.

---

### Post by Toadmund on 2007-04-02
I am having the same GRUB pollution issue, I went into the GRUB,
```
 sudo gedit /boot/grub/menu.lst
``` 

I put my main bootup at the start of the list, but it's not default?
Just easy to find real quick as it's at the top during boot-up.

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
default         8

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro

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
# defoptions=splash vga=791

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
# updatedefaultentry=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-13-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-13-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.20-13-generic
savedefault

title		Ubuntu, kernel 2.6.20-13-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-13-lowlatency root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.20-13-lowlatency
savedefault

title		Ubuntu, kernel 2.6.20-13-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-13-lowlatency root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.20-13-lowlatency

title		Ubuntu, kernel 2.6.20-13-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-13-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.20-13-generic

title		Ubuntu, kernel 2.6.20-12-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-12-lowlatency root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.20-12-lowlatency
savedefault

title		Ubuntu, kernel 2.6.20-12-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-12-lowlatency root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.20-12-lowlatency

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.20-12-generic
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault

title		Ubuntu, kernel 2.6.15-28-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.15-28-amd64-generic

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro splash vga=791
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=UUID=1544108e-8b31-4a27-bd87-942b80e8120a ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
What a mess! Went into synaptic to install linux-restricted-modules and it got even messier.
How do I set the 2.6.20 as default boot, can I delete all the rest (besides windows)
Everytime I update it adds, not replaces my boot choice menu, it gets confusing!
Thanks.

---

### Post by Campingman on 2007-04-02
Hi,
I do not know if I am reading this correct so apologies if this is a stupid answer.
To change the default op system you change the number after the default entry (8 in your list) to the position in the boot list that the op system is.  EG if you want to boot the first listed item as default change it to 1

---

### Post by dstew on 2007-04-02
I think grub counts starting at 0, so the first item on the list would be 0, not 1.

Remove the unwanted/unused kernels using Synaptic. When the old kernels are removed, the menu.lst file is also updated.

---

### Post by Toadmund on 2007-04-02
So, you folks are saying that if I put (0) or (1) in where it says (8 ) at the very top of /boot/grub/menu.lst the first item in the list will load, instead of the ninth item?

Yeah? So, is it 0 or is it 1?
One of you is right, which means one of you is also wrong.

Could I just delete what I don't want instead of going to synaptic?


OK, I see that in synaptic I downloaded restricted modules for older Ubuntu versions.

---

### Post by Toadmund on 2007-04-03
Seems I was wrong:) 
But I did put the one I want to boot at the top of the list, but it didn't make it default.

The number at the end, if I set that to (0) or (1) will it boot he first item in the boot list?:
from:```
 sudo gedit /boot/grub/menu.lst
```
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         8
```

---

### Post by dstew on 2007-04-03
**default 0** will make the first item in the list the one that will boot if you do nothing.

---

### Post by Toadmund on 2007-04-03
Thank you, I just needed some reassurance, I wouldn't want to find myself in a non-bootable state.
Like me in the morning without coffee.

---

