---
title: "uninstalling linux to reinstall later?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-19
HI.. I hove done something seriously wrong and now I want to uninstall linux.. for two resons.
one i want the hard drive space.
two. I want to reinstall it as something happened during the first installation.

My question is How do completely uninstall linux?
should i use gparted? pls help

EDIT: will reinstalling ubuntu form the live cd work just as well?
I mean , will it just ***completely*** overwrite the current ubuntu without leaving anything behind? (that is what i want)

---

### Post by Oldsoldier2003 on 2008-03-19
> **mahela007 said:**
> HI.. I hove done something seriously wrong and now I want to uninstall linux.. for two resons.
one i want the hard drive space.
two. I want to reinstall it as something happened during the first installation.

My question is How do completely uninstall linux?
should i use gparted? pls help

to completely uninstall
1) boot with live cd or GParted live CD then just delete the ubuntu partition and swap partition
2) boot with a windows cd and go to the recovery console and do fixmbr or fdisk /mbr

if you reinstall from the live cd you can overwrite the current Ubuntu , it will format the partition so it will be fresh with no traces of the old installation

---

### Post by linuxtoindia on 2008-03-19
> **mahela007 said:**
> HI.. I hove done something seriously wrong and now I want to uninstall linux.. for two resons.
one i want the hard drive space.
two. I want to reinstall it as something happened during the first installation.

My question is How do completely uninstall linux?
should i use gparted? pls help

EDIT: will reinstalling ubuntu form the live cd work just as well?
I mean , will it just ***completely*** overwrite the current ubuntu without leaving anything behind? (that is what i want)
o you have any othere os on your hardisk?
and any data?
 if yes then pls mention..
 if no then download norton partition magic i suggest .. boot from it take any one of ur partition or create after wiping hard disk!
and then reinstall
with ext3 partition

---

### Post by markharding557 on 2008-03-19
> **mahela007 said:**
> HI.. I hove done something seriously wrong and now I want to uninstall linux.. for two resons.
one i want the hard drive space.
two. I want to reinstall it as something happened during the first installation.

My question is How do completely uninstall linux?
should i use gparted? pls help

EDIT: will reinstalling ubuntu form the live cd work just as well?
I mean , will it just ***completely*** overwrite the current ubuntu without leaving anything behind? (that is what i want)

all you have to do is run the live cd and install from this,use its built in partitioner(no need for gparted or partition magic)and if you have windows or another o/s it will detect it as before and no it won't leave anything behind provided all partitions are formatted

---

### Post by mahela007 on 2008-03-20
the way I understand it when i uninstall or delete the partition brub wont change. to fix grub i have to use w\the windows cd. Heres the problem.
i dont have the windows CD? so after I remove linux how do i fix grub?

---

### Post by Ardrias on 2008-03-20
If you dont have a Windows CD, why not take some time to fix the problems you're having with Linux? Most likely there's people here to help you. :)

---

### Post by markharding557 on 2008-03-20
> **mahela007 said:**
> the way I understand it when i uninstall or delete the partition brub wont change. to fix grub i have to use w\the windows cd. Heres the problem.
i dont have the windows CD? so after I remove linux how do i fix grub?

if you have windows already installed on a partition the ubuntu installer will detect  and add it to the boot loader when it reinstalls grub so you do not need a windows cd unless you have deleted your windows partition.
windows cd does not fix or install grub.
you have not made it very clear  whether you intend to reinstall ubuntu or have windows only in the case of the latter you would need a windows cd to fix mbr

---

### Post by mahela007 on 2008-03-21
I already have windows XP and liinux. I want to uninstall linux and then reinstall it bcos i messed it up

---

### Post by The Cog on 2008-03-21
Grab this CD:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
You can use this to replace the existing bootloader. It can replace the Ubuntu GRUB with one that can boot Windows.

---

### Post by mahela007 on 2008-03-21
how do you use it?

---

### Post by The Cog on 2008-03-21
It's a live CD. Boot from it and use the menus. Choose supergrub with help. IT has options to boot Windows or Linux and to replace the bootloader e.g. "MBR+Windows".

---

### Post by markharding557 on 2008-03-21
> **mahela007 said:**
> I already have windows XP and liinux. I want to uninstall linux and then reinstall it bcos i messed it up

if you want to reinstall ubuntu then you need only use the ubuntu installer it will over write the previous linux installation with a new one while retaining windows simple as

---

