---
title: "YES! windows and grub sorted. almost"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-26
i have my windows sorted!
i followed small instructions and at boot it was called '1' so i didnt forget. creative eh?

anywaycsorted my grub out and ubuntu and windows appear.
but windows is the WRONG one!
the one with missin hal.dll was

'windows XP pro...' <--this one dosent boot
and not
'1' <--my creative name...and this one boots!

why isnt it appering?
it works! i was just on windows!

---

### Post by molly_001 on 2007-06-26
There are two records in the mbr of a bootable dialogue.  This is standard after the whole hal.dll thing plus needing to sort Windows out (after hal.dll) plus a GRUB install.  Just don't use the old Windows XP Pro tag when selecting where to boot and you'll be fine.

Or you could always edit out the offending entry in
   /boot/grub/menu.lst

Don't edit menu.lst unless you know what you're doing, though.

---

### Post by freebird54 on 2007-06-26
Not quite sure what your problem is - but I assume that the display of choices in grub doesn't match your system correctly?  If you open a terminal and post the results of

```
cat /boot/grub/menu.lst
```

we might be able to tell you wahat to put to run the right one (1) thereafter....

It wouldn't hurt to post :

```
sudo fdisk -l
```

either... just in case!

---

### Post by skymera on 2007-06-26
i dont care how my Grub menu looks. 
as long theres what  i nee

i dont the frist command

```
 scott@scott-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=98bf1b10-c841-47fd-bb93-413be108e730 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=98bf1b10-c841-47fd-bb93-413be108e730 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=98bf1b10-c841-47fd-bb93-413be108e730 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=98bf1b10-c841-47fd-bb93-413be108e730 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=98bf1b10-c841-47fd-bb93-413be108e730 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

and second

```
 scott@scott-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               7        5743    46082452+   7  HPFS/NTFS
/dev/sda2   *        5744       15990    82309027+  83  Linux
/dev/sda3           15991       19452    27808515    f  W95 Ext'd (LBA)
/dev/sda5           15991       16245     2048256   82  Linux swap / Solaris
/dev/sda6           16246       19452    25760196   83  Linux

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10011    80413326    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 521 MB, 521404416 bytes
204 heads, 52 sectors/track, 24 cylinders
Units = cylinders of 10608 * 2048 = 21725184 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          24      509080    b  W95 FAT32
scott@scott-desktop:~$ sudo fdisk -l

```

---

### Post by freebird54 on 2007-06-26
Still guessing a bit (not sure what isn't working) but I'll assume that when you choose  **Windows XP Media Center Edition** you get the hal error.  So - here are a couple of possible entries that would work from what I see of your disk layout..  Either (see bolded parts)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
**root            (hd0,0)**
savedefault
makeactive
chainloader     +1
```

OR

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
**root            (hd1,0)**
savedefault
makeactive
chainloader     +1
```

to edit this file (if you haven't been doing this all along) first.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup070626
gksudo gedit /boot/grub/menu.lst
```

and paste in the more likely of the 2 changed pieces above.  The first one is to start it correctly off the FIRST hard drive, the second off the SECOND hard drive.  (Grub starts counting at 0,0 - the sytem counts from a,1).

Then remove the incorrect chunk, save, and restart to test.  OK?

**_If this does not match your problem, please clarify!_**

---

### Post by skymera on 2007-06-26
i think i found the problem.
in grub i edited one of the options.

and old kernel -15

it was (hd0,2) first....no boot but then.... (hd0,1) and BOOT!

will this work for the windows?

---

### Post by freebird54 on 2007-06-26
If you enter the right value, it should.  From what you posted before (the fdisk -l output) my 2 best guesses are (hd0,0) and (hd1,0) - but I don't know what you put where, or when for sure... :)  Give them a try.  

BTW - if you hit escape when grub is showing, you can make changes to test right there and then, and see what boots.  You still make permanent changes in /boot/grub/menu.lst though....

---

### Post by skymera on 2007-06-26
nice, this is like a game.

not one that i enjoy.

thanks for the help :)

---

### Post by freebird54 on 2007-06-26
Well - you may not love the game  - but WINNING it is still fun! :)

Let me know when you have it sorted...If this does not match your problem, please clarify!

---

### Post by skymera on 2007-06-26
o i believe i have 2 grub menus?>??

my first looks like this:
```

Ubuntu 2.6.0-16 generic
Ubuntu 2.6.0-16 generic (Recover mode)
Ubuntu 2.6.0-15 generica
Ubuntu 2.6.0-15 generic (Recovery mode)

other Operating Systems

Windows Xp Meida Centre....blah 
```

if i put windows as (hd1,0)!!! it takes me to ANOTHER menu

which has

```

1
windows media...meh

```

1 <--my NEW windows that i made since i broke my other
windows media center edition <---DOSENT work, missing HAL.dll.

i need to get rid of the second one and replace with the creative one, dubbed, '1'

confusing?

---

### Post by freebird54 on 2007-06-26
Looks to me like the Grub fix is done.  When you choose Windows Media (etc) it boots correctly to Windows, but the WINDOWS BOOTLOADER shows up next, and contains your 1 that works and one that doesn't.  If you edit BOOT.INI on your Wndows, you can remove the entry that doesn't work, and it will default into the one that does.

Hope that clears it up!

---

### Post by skymera on 2007-06-26
but when i do select windows and i get my srecond grub thing.

thats 'default' next time i boot that shows up. not the one with ubuntu etc.

maybe if i do edit boot.ini in windows it will merge since there wil be olny one

---

### Post by freebird54 on 2007-06-26
Weird - it must be changing which drive is the boot drive when you choose Windows....  Not sure how to avoid that!  What does you BIOS say about boot drive order etc?  If you can start from drive (hd0) and 'lock' it, you should be OK from there...

---

### Post by skymera on 2007-06-26
anywhoo
got into windows, deleted the dead version of windows
heres what my boot.ini looked like

```
 [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="1" */fastdetect*
**multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect** 
```

i deleted the one in bold
and added italics.

it fails too boot again. how tragic .
i cant edit boot.ini in ubuntu either, so i cant reevrt to how it was... damn

---

### Post by freebird54 on 2007-06-26
No reason you can't edit boot.ini from Ubuntu - assuming you have the Win partition mounted.  Boot.ini can be fussy about the strangest things - like blank lines and extra characters - any chance that happened?

Also- if you have trouble editing boot.ini from Ubuntu, you can boot to Win command line and fix it from there (off a floppy or an XP CD).

BTW - here is the relevant boot.ini from my dual boot (actually quad boot, but who's counting)..
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Not even a space after /fastdetect - and certainly not a newline.. :)

---

### Post by skymera on 2007-06-26
had a play aaround with grub

it was (hd0,0) which baffles me....im currently in windows now.

anyway want to say thanks for all the help you gave me..freebird
well now,been trying to fix since abiout 9pm and now its 1:33AM ...cya

-Scott

---

