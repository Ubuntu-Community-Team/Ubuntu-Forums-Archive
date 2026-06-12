---
title: "Question with grub"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-03
I am running a XP/ Ubuntu 7.04 dual-boot.  When my computer boots up, it shows the GRUB menu where i am to select which OS to boot.  There are about 6-7 options on the list, but two that i would actually use:

Windows XP
Ubuntu version 7.04

Is there anyway to remove the other choices?
 
and

Ubuntu is selected as my default(i believe) If i dont select an OS within 10 seconds it runs ubuntu automatically.  Shouldnt windows be the default OS?

---

### Post by Shazaam on 2007-07-03
# out the ones you don't want in Menu.lst. Don't # the one that you boot into:D

---

### Post by Raineer on 2007-07-03
I wouldn't recommend removing the "Recovery Mode" options as you are guaranteed to need them the next day :)

You can edit these by running the following:
```
gksudo gedit /boot/grub/menu.lst
```

And scrolling down to the bottom to comment out what you don't like (I would comment out with double #'s), like:
```
##title           Ubuntu, kernel 2.6.20-15-generic
##root            (hd0,0)
##kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=lotsof numbers
##/boot/initrd.img-2.6.20-15-generic
##quiet
##savedefault    
```
Keep in mind that removing a choice may cause your "default" choice to change at the top of the file, explained like this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0                                                    
```

---

### Post by ITdrummer on 2007-07-03
Thats all i needed to know! Thanks guys

---

### Post by ITdrummer on 2007-07-03
> **Raineer said:**
> 
And scrolling down to the bottom to comment out what you don't like (I would comment out with double #'s)


Why double #'s.  Wouldnt a single # work just as good?

---

### Post by Raineer on 2007-07-03
Grub takes the time to use double and single, so I don't mind sparing the extra 6 bytes on my HDD :)

---

### Post by nphx on 2007-07-03
[SIZE="3"][COLOR="Red"]**NOTE:** [/COLOR]Before you edit the **menu.lst**, you should back up the file so you can revert when you need to. Do this by entering:[/SIZE]

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```


The Grub menu configuration is stored in **/boot/grub/menu.lst**

Around line 14 you'll see **default 0**, where zero is the first choice of OS to boot to from the Grub menu list:

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]

It's not a good idea to remove the rest of the kernel options because you'll never know when you need them, instead you can hide them with a blank line OS entry. For example:

> [COLOR="DeepSkyBlue"]title		Ubuntu 7.04 (Feisty Fawn), kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=d0c2af16-87d3-4191-918a-179e644d0b99 ro quiet splash vga=791
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/COLOR]

[COLOR="Red"]title            
root[/COLOR]
[COLOR="Lime"]

title           Other utility operating systems:
root[/COLOR]


title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=d0c2af16-87d3-4191-918a-179e644d0b99 ro single vga=792
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=d0c2af16-87d3-4191-918a-179e644d0b99 ro quiet splash vga=791
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=d0c2af16-87d3-4191-918a-179e644d0b99 ro single vga=791
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet


The section in the red is the blank OS title, it hides whatever is bellow it, but you can still access it easly just by pressing down arrow all the way to the hidden selection in the Grub menu during boot.

The blue section is the OS's you want to show up in the Grub menu during boot. They are recognized in the Grub configuration file as 0 and 1. 

0 = Ubuntu 7.04 (Feisty Fawn), kernel 2.6.20-16-generic
1 = Microsoft Windows XP Professional

So if I wanted Windows to be the **default** choice I would change line **14** in the** /boot/grub/menu.lst** to **1**. For example:

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		1[/COLOR]

To edit the file **/boot/grub/menu.lst**:

```
gksu gedit /boot/grub/menu.lst
```

---

