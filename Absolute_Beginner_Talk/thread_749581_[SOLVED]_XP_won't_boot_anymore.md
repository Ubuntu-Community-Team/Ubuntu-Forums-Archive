---
title: "[SOLVED] XP won't boot anymore?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Locke_99GS on 2008-04-08
Hello all. I installed 8.04 a few weeks ago and immediately fell in love with it. Everything "just worked", in particular the plug'n'play cellphone GPRS connection and Bluetooth. It plays most of my games (some with some effort) except it wont play Sims 2 - the wife insists on playing it - but I digress.

After the install, everything worked OOTB, even detecting XP and properly adding it to GRUB. Windows would boot fine for about a week or so, then one day the Mrs. told me she couldn't start XP. I don't know for how long it didn't work, but I can tell you I never messed with anything relating to GRUB. (unless an update broke it?) 

When I select the Windows XP option when GRUB loads, it drops me to a black screen and just hangs. No drive access, nothing.

Here is my menu.lst:

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
# kopt=root=UUID=de486823-a70c-4d51-876f-dfb1c6ba0018 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=de486823-a70c-4d51-876f-dfb1c6ba0018 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=de486823-a70c-4d51-876f-dfb1c6ba0018 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Any help is greatly appreciated, thanks in advance.

---

### Post by OffAxis on 2008-04-08
are those entries for the hard drives correct?
2 hard drives 
xp on disk 1 partition 1 (hd0,0)
ubuntu on disk 2 partition 1 (hd1,0)
?

if that's not right, then you'll need to point the xp entry to the appropriate hard drive/ partition for it.

---

### Post by ELF_O8 on 2008-04-08
> **Locke_99GS said:**
> ```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I think the partition "root" is reading for Windows is wrong.
"root" should be directed as such:

```
title		Microsoft Windows XP Home Edition
[highlight]root		(hd0,1)[/highlight]
savedefault
makeactive
chainloader	+1
```

---

### Post by Locke_99GS on 2008-04-08
> **OffAxis said:**
> are those entries for the hard drives correct?
2 hard drives 
xp on disk 1 partition 1 (hd0,0)
ubuntu on disk 2 partition 1 (hd1,0)
?

if that's not right, then you'll need to point the xp entry to the appropriate hard drive/ partition for it.

Yeap, two hard discs. hd0,0 is correct for XP. I had XP installed prior to linux, it is on the primary master first partition. Ubuntu is on the primary slave first partition.

> **ELF_O8 said:**
> I think the partition "root" is reading for Windows is wrong.
"root" should be directed as such:

```
title		Microsoft Windows XP Home Edition
[highlight]root		(hd0,1)[/highlight]
savedefault
makeactive
chainloader	+1
```

hd0,1 would be the second partition of the first disk, which is not my case. 



I do appreciate the effort though, guys.

---

### Post by Joeb454 on 2008-04-08
Your menu.lst hasn't changed with any of the Kernel updates has it?

This is the problem with running a beta in a dual boot :p Trust me, I've done it twice :D

I'll take a look at mine and see if it looks similar (difference being I have Vista not XP :))


**EDIT:**

Just realised - Have you checked the XP partition for disk errors etc?

And what happens when you try and boot XP :)

---

### Post by OffAxis on 2008-04-08
maybe it's not a grub / ubuntu problem at all; maybe there's an issue with the windows install or the windows hard drive.
I'd try circumventing the grub (ubuntu drive) completely and boot straight off the first hard drive. You should be able to change the boot sequence in the BIOS and have it boot to the windows drive.
What happens?


Whenever you're messing with grub and windows it's good to have 2 things:
1. Super-grub disk
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

2. A liveCD, and Know how to fix the grub off it to get back into ubuntu.
```
sudo grub
grub>root(hd1,0)
grub>setup(hd1)
grub>quit
```

---

### Post by Locke_99GS on 2008-04-08
> **Joeb454 said:**
> Your menu.lst hasn't changed with any of the Kernel updates has it?

This is the problem with running a beta in a dual boot :p Trust me, I've done it twice :D

I'll take a look at mine and see if it looks similar (difference being I have Vista not XP :))


**EDIT:**

Just realised - Have you checked the XP partition for disk errors etc?

And what happens when you try and boot XP :)

I'm not aware of it changing with any updates, but I'm not positive. The Windows section *appears* to be the same as it was when I installed, but I never made a back-up to revert/compare to. 

I have not checked the XP drive for errors. How would I go about this in Ubuntu? The entire drive (ntfs) is accessible with no hitch through Nautilus, and the necessary NTLDR files are in place on the disk as well. 

When I try to boot XP, the screen immediately goes black. That's it, nothing else.

---

### Post by Locke_99GS on 2008-04-08
> **OffAxis said:**
> maybe it's not a grub / ubuntu problem at all; maybe there's an issue with the windows install or the windows hard drive.
I'd try circumventing the grub (ubuntu drive) completely and boot straight off the first hard drive. You should be able to change the boot sequence in the BIOS and have it boot to the windows drive.
What happens?


It could be a Windows problem or drive problem, but I never changed the boot order in the BIOS during the linux install, so GRUB (stage 1) should be on the Windows drive, (first bootable, hd0,0) displacing the NT bootloader.

---

### Post by OffAxis on 2008-04-08
okay, then how about that Super Grub disk?
If I recall, you can boot off it, then choose the windows drive.

---

### Post by hamishw on 2008-04-08
Hey,
just a thought but your MBR might be broke. You could fix it by installing ms-sys. 
Use in terminal 

[I]sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda[/I]

where sda represents your windows partition. This has worked for me a few times!!!

Also, if you really want to boot Windows first perhaps just to check, you could use gparted to check your boot flags and make sure that the win partition is flagged as the primary boot partition.......

However, I'm no expert, so don't take my word for it!!!!

Cheers,

Hamish

---

### Post by adrian15 on 2008-04-10
> **Locke_99GS said:**
> 
Here is my menu.lst:

```

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Any help is greatly appreciated, thanks in advance.

Please use:
```

title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
makeactive
chainloader	+1
boot

```
instead.

adrian15

---

### Post by Locke_99GS on 2008-04-12
I burned SuperGrubDisk to a CD, and *I am able to boot Windows with it*. I went through SGD's series of .lst's and changed my menu.lst accordingly. My menu.lst's sequence to boot Windows is now identical to the sequence of grub commands used by SGD to boot Windows, but it still doesn't work.

In my copying SGD's stuff to my own, my Windows title section ended up looking just as your recommended change, adrian15, but to no avail. 

I am able to now get to the NTLDR's "Windows shutdown unexpectedly" menu (or whatever it says) where it gives me option to boot safe mode, normal mode, and last known good configuration, but whichever option I choose, it locks up - no black screen this time. 

I have made little progress with this so far. I will try the ms-sys thing mentioned at the end of the last page, but if that doesn't work I will wait for the full release of Hardy in 12 days, backup my home directory, reinstall the Windows bootloader, then do a full clean install of 8.04, grub and all. I don't see why this won't work, as when I last installed Hardy, the bootloader worked flawlessly.



I thank you all for your assistance thus far, and when I do get this firgured out - even if I have to reinstall - I'll be sure to resolve the thread.

---

### Post by adrian15 on 2008-04-13
> **Locke_99GS said:**
> I burned SuperGrubDisk to a CD, and *I am able to boot Windows with it*.

Which option did you use?

> **Locke_99GS said:**
> 
 I went through SGD's series of .lst's and changed my menu.lst accordingly. My menu.lst's sequence to boot Windows is now identical to the sequence of grub commands used by SGD to boot Windows, but it still doesn't work.


Try the GRUB SOLUTION from [Howto Boot Windows from a second hard disk](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_From_A_Second_Hard_Disk), it might work for you.

Sometimes the hard disk boot order differs when booting from cdrom than from when booting from hard disk.

adrian15

---

### Post by Zralou on 2008-04-13
Just as an FYI, i'm running Hardy on a dual boot too.  Last night after running the update process, it asked me if I wanted to 'update' the grub menu.lst or leave the 'locally changed' version in place.  I chose leave it alone.
So it is possible your update did change the grub and now the NTLDR is corrupt in XP.

Sara Lou

---

### Post by nge on 2008-04-13
Actually, it probably could be as simple as :

1. Repair the XP installation

2. Then, boot into Ubuntu Live CD, open Terminal, then:

3. sudo grub

4. find /boot/grub/stage1
it will return (hdx,y)

5. root (hdx,y)

6. setup (hdx,y)

7. setup (hd0)   (presuming that your first boot device is hd0)

8. quit

9. Reboot your computer.

---

### Post by Locke_99GS on 2008-04-27
I never did get XP to boot from my local grub. Since I was running the Hardy beta and had intended on doing a fresh install of the official release, I repaired the NT bootloader on the MBR and tested it. It booted straight to XP on reboot. Then I reformatted my ext3 drive and installed Hardy full on it. The installer did everything correctly - I can now boot to XP with grub when I choose.

Thanks for all the advise guys, and sorry I couldn't seem to find a solid solution that didn't involve starting over. No sweat for me, as I intended to anyways, but obviously not helpful to others not willing to start over.

---

