---
title: "[SOLVED] Dual booting?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by iainr86 on 2007-12-30
I've just installed xubuntu onto a separate hard drive from my windows installation, but when i start my computer up it boots straight into xubuntu. when it come up and says press esc to enter grub it only gives me the option of booting xubuntu, xubuntu recovery mode and something else, no windows. How do i get back into windows??

---

### Post by LaRoza on 2007-12-30
Two ways:

The easy (but PITA way):

Select your Windows to boot. Press the correct key combo for your BIOS for this.

Best way: Add Windows to grub.

Post the output of these two commands:

```

sudo fdisk -l

```
(Lowercase L)

```

less /boot/grub/menu.lst

```

I will make it easy for you, and will explain the commands after if you want :)

---

### Post by iainr86 on 2007-12-30
awesome thanks. here goes:

iain@iain-desktop:~$ sudo fdisk -l
[sudo] password for iain:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15b815b7

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7296    58605088+   7  HPFS/NTFS
/dev/hda2            7297       14592    58605120    f  W95 Ext'd (LBA)
/dev/hda5            7297       14592    58605088+   7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7a6b7a6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7166    57560863+  83  Linux
/dev/hdb2            7167        7297     1052257+   5  Extended
/dev/hdb5            7167        7297     1052226   82  Linux swap / Solaris




and the next one:

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
# kopt=root=UUID=f7862c87-980c-445b-bd09-7e0158091901 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f7862c87-980c-445b-bd09-7e0158091901 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f7862c87-980c-445b-bd09-7e0158091901 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Hope that means more to you than it does to me!!

---

### Post by Liolikas on 2007-12-30
Just remove all # from this part and save:
```

#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1

```

---

### Post by iainr86 on 2007-12-30
ah right i think i see what thats doing. only problem now is it wont let me save any changes, think i only have read only access. i need to log in as root right? whats the root password?

---

### Post by LaRoza on 2007-12-30
> **iainr86 said:**
> ah right i think i see what thats doing. only problem now is it wont let me save any changes, think i only have read only access. i need to log in as root right? whats the root password?


Add this to the END, don't uncomment it:
```

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

```

Run this command:

```

gksudo gedit /boot/grub/menu.lst

```

(Enter the password you made when you installed)

---

### Post by iainr86 on 2007-12-30
ummmm..... do i edit this in the terminal window? it wont let me type anything? or open it in a text editor in which case it wont let me save it?

sorry for being stupid!!

---

### Post by LaRoza on 2007-12-30
> **iainr86 said:**
> ummmm..... do i edit this in the terminal window? it wont let me type anything? or open it in a text editor in which case it wont let me save it?

sorry for being stupid!!

The last commend I gave, gksudo gedit /boot/grub/menu.lst will open your text editor as root.

Add the lines I gave to the end of the file and save it.

Yes, you enter the commands in the terminal or in the box you get when your press Alt + F2.

EDIT, I see the confusion, run the command, then add the lines.

---

### Post by iainr86 on 2007-12-30
ok i've tried this loads of times to make sure i'm not being stupid, i type in 
 gksudo gedit /boot/grub/menu.lst
then a window comes up asking me for my password, so i put that in and.... nothing. No text editor comes up. is this the command to open it in mousepad? cos thats the app that it opens in when i open it through the file system. thanks for your patience!

---

### Post by iainr86 on 2007-12-30
yep, ive tried to open gedit and i get:

The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
bash: gedit: command not found
iain@iain-desktop:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gedit

(i cant just install it because my internet is also not working, see my other post!)

can someone tell me an alternative way?

---

### Post by iainr86 on 2007-12-30
ok that time i was genuinely being stupid.

i used gksudo mousepad /boot/grub/menu.lst and its let me edit it. now to restart and see if its worked

---

### Post by meindian523 on 2007-12-30
Ok,we can use other editors to solve your problem:

In terminal:

```
sudo vim /boot/grub/menu.lst
```

Press "a"

Type in the text given by LaRoza

Press "Esc"

Type

```
:wq
```

and you are done.

For an explanation:
```

vim is the VIsual editor iMproved

a is for entering into typing mode

Esc is for entering into command mode

:wq is for Writing and Quitting

```
Hope this helps.

Edit:Please ignore post if issue resolved.Please mark the thread solved if issue resolved.

---

### Post by LaRoza on 2007-12-30
Sorry, I didn't realize you were using Xubuntu, and didn't know the default text editor. I personally use Vim, but I thought that would be more confusing for you.

---

