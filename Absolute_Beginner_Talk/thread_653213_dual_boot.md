---
title: "dual boot"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-29
vista primary HD 
linux second HD

only boots to Linux

can you steer me to a guide?

---

### Post by taurus on 2007-12-29
Can you post the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo cat /boot/grub/menu.lst
```

---

### Post by hums07 on 2007-12-29
.

---

### Post by frenchsquared on 2007-12-29
when I tpyed the first line it asked for a password, but It wouldnt let me type anything

it never gave an option to pick a HD
I dont want to go into the bios to change the HD's everytime

---

### Post by PeterJS on 2007-12-29
> **frenchsquared said:**
> when I tpyed the first line it asked for a password, but It wouldnt let me type anything


Don't worry about that, it is letting you type it just isn't giving you any visual feed back that it's receiving keystrokes, that's a security feature to make shoulder surfing harder.

---

### Post by Dr Small on 2007-12-29
> **frenchsquared said:**
> when I tpyed the first line it asked for a password, but It wouldnt let me type anything

it never gave an option to pick a HD
I dont want to go into the bios to change the HD's everytime
Hi, check out this link:
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

---

### Post by frenchsquared on 2007-12-29
gordon@Asus:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
240 heads, 63 sectors/track, 20667 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20666   156234928+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23786   191061013+  83  Linux
/dev/sdb2           23787       24792     8080695    5  Extended
/dev/sdb5           23787       24792     8080663+  82  Linux swap / Solaris
gordon@Asus:~$
gordon@Asus:~$ sudo cat /boot/grub/menu.lst
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
timeout         3

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
# kopt=root=/dev/sdb1 ro

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
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
gordon@Asus:~$

---

### Post by frenchsquared on 2007-12-29
i dont have any im set up yet sorry,
this is really knew to me

---

### Post by zipperback on 2007-12-29
> **frenchsquared said:**
> vista primary HD 
linux second HD

only boots to Linux

can you steer me to a guide?

Yes. 

If you want to create a dual boot system check out these links.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

The following link has several different tutorials which deal with dual booting.
Linux, XP, Vista, etc.....
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

- zipperback
:popcorn:

---

### Post by PeterJS on 2007-12-29
> **frenchsquared said:**
> 

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
gordon@Asus:~$


If you look at the example at the top of the quote there that's pretty much what you're looking for, copy that and put it after the automagic kernel's section, uncomment it, and you should be 90% of the way there. The root (hdX,X) line tells grub where to look for windows, the first number is the disk number and the second is the partition number so hd0,0 would be the first parition of the first disk, that's probably what you're looking for, but experiment around with it a bit if that's not right.

---

### Post by frenchsquared on 2007-12-29
thanks
will play for a few minute

I have searched for info and everything says to install windows then linux 
linux will make the dual boot, that might work if you partition the HD but it didnt work for me

and if you red the original questio,n i asked if someone would send links to instruction or a sticky

thank you to the others who have been helpful
Im certain once i get the basic I will be ok
but currently I am very overwelmed

---

### Post by teryowen on 2007-12-29
i dont see the problem here just while you're in linux in terminal:

gksudo gedit /boot/grub/menu.lst

and add the following piece of code:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title                Windows
root                (hd0,0)
savedefault
makeactive
chainloader        +1

```

---

### Post by frenchsquared on 2007-12-29
i read the links and there not correct

1. this is vista not xp
2. I didnt partition the HD I installed an a seperate HD
3. the isnt a boot screen it just goes to the ubuntu login

I understand the examples but not how to edit the boot file 
terminal displays it, but nothing has told me how to change it

and yes vista should be HD(0,0)

---

### Post by teryowen on 2007-12-29
try this in terminal do:

sudo nautilus

this will open up a manager, go to the folder /boot then grub and then double click on menu.lst and it should be pertty straight forward to edit it.

---

### Post by frenchsquared on 2007-12-29
sorry guys

ok 
I added what it said

now it boots into vista
still no boot screen

---

### Post by teryowen on 2007-12-29
what boot screen are u talkin about? the Ubuntu splash?

---

### Post by frenchsquared on 2007-12-29
the screen shoots show a black screen with an option to select linux or windows

if you do a dual boot with vista and xp that start screen is called a boot screen

---

### Post by PeterJS on 2007-12-29
Ah that's the grub menu, if you take a look at your config you'll see:
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

If you comment out the hide menu line, and change the 3 second time out to something longer, like say 10 you should be good to go.

---

### Post by teryowen on 2007-12-29
oh thats completely different, thats when you have vista manage your booting it adds an entry of XP to its options which is why u seethe options.

here with linux what you have is a GRUB loader, which is just a text based menu to choose your boot option.

is this wat you're talking about, because as long as you see this grub menu and are able to boot into all your OS's fine then you're good.

EDIT:

Now that i see PeterJSs post i understand your problem and what he said it right just do that.

---

### Post by frenchsquared on 2007-12-29
GRUB boot menu

---

### Post by frenchsquared on 2007-12-29
> **PeterJS said:**
> Ah that's the grub menu, if you take a look at your config you'll see:
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

If you comment out the hide menu line, and change the 3 second time out to something longer, like say 10 you should be good to go.

you rock
that was the problem
everything is working now 
thank sorry, but I didnt see anything like this in the stickies

---

### Post by meierfra on 2007-12-29
Please move your Vista item above the line:

### BEGIN AUTOMAGIC KERNELS LIST

Otherwise your   Vista item will disappear  from menu.lst after the next kernel update. 
Everything between 

### BEGIN AUTOMAGIC KERNELS LIST

        and 

### END DEBIAN AUTOMAGIC KERNELS LIST

gets  rewritten during kernel update.

You can  test this: Just run

```
sudo  update-grub
```

in a terminal and you will see that the Vista item is  gone.


If you want to boot into "Ubuntu" by default (and not to Vista) move  the Vista item to the very end of the file.

---

