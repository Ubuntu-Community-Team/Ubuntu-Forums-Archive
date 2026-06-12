---
title: "virtualbox sata harddrive?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by oisuxx on 2007-11-05
is it possible to have my physical sata hdd appear in virtualbox?

im trying to use windows programs that are located on there. all im seeing is vdi files...
any help would be appreciated

---

### Post by Skweek on 2007-11-06
Hi,

Section 9.9 in the Vbox user manual describes setting up a physical HD for use with virtualbox. (available via the help menu).

Extract follows;

9.9.1. Access to entire physical hard disk
While this variant is the simplest to set up, you must be aware that this will give a guest operating system direct and full access to an entire physical disk. If your host operating system is also booted from this disk, please take special care to not access the partition from the guest at all. On the positive side, the physical disk can be repartitioned in arbitrary ways without having to recreate the image file that gives access to the raw disk.
To create an image that represents an entire physical hard disk (which will not contain any actual data, as this will all be stored on the physical disk), on a Linux host, use the command
[B]VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
        -rawdisk /dev/sda[/B]
This creates the image /path/to/file.vmdk (must be absolute), and all data will be read and written from /dev/sda.
On a Windows host, instead of the above device specification, use e.g. \\.\PhysicalDrive0.
Creating the image requires read/write access for the given device. Read/write access is also later needed when using the image from a virtual machine.
Just like with regular disk images, this does not automatically register the newly created image in the internal registry of hard disks. If you want this done automatically, add -register: 
[B]VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
        -rawdisk /dev/sda -register[/B]
After registering, you can assign the newly created image to a virtual machine with 
VBoxManage modifyvm WindowsXP -hda /path/to/file.vmdk
When this is done the selected virtual machine will boot from the specified physical disk.

---

### Post by PokerJoker on 2007-11-07
> **Skweek said:**
> Hi,

Section 9.9 in the Vbox user manual describes setting up a physical HD for use with virtualbox. (available via the help menu).

Extract follows;

9.9.1. Access to entire physical hard disk
While this variant is the simplest to set up, you must be aware that this will give a guest operating system direct and full access to an entire physical disk. If your host operating system is also booted from this disk, please take special care to not access the partition from the guest at all. On the positive side, the physical disk can be repartitioned in arbitrary ways without having to recreate the image file that gives access to the raw disk.
To create an image that represents an entire physical hard disk (which will not contain any actual data, as this will all be stored on the physical disk), on a Linux host, use the command
[B]VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
        -rawdisk /dev/sda[/B]
This creates the image /path/to/file.vmdk (must be absolute), and all data will be read and written from /dev/sda.
On a Windows host, instead of the above device specification, use e.g. \\.\PhysicalDrive0.
Creating the image requires read/write access for the given device. Read/write access is also later needed when using the image from a virtual machine.
Just like with regular disk images, this does not automatically register the newly created image in the internal registry of hard disks. If you want this done automatically, add -register: 
[B]VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
        -rawdisk /dev/sda -register[/B]
After registering, you can assign the newly created image to a virtual machine with 
VBoxManage modifyvm WindowsXP -hda /path/to/file.vmdk
When this is done the selected virtual machine will boot from the specified physical disk.

I installed virtualbox using apt-get, and got the ose version. GUI works, but i want to do stuff from manual 9.9 using "vboxmanage internalcommands" but it seems the only internalcommands my version has are: 

> alex@scaleo-gg:~/vm$ sudo vboxmanage internalcommands createrawvmdk -filename /home/alex/vm/file.vmdk -rawdisk /dev/sda -partitions 1
VirtualBox Command Line Management Interface Version 1.5.0_OSE
(C) 2005-2007 innotek GmbH
All rights reserved.

Usage: VBoxManage internalcommands <command> [command arguments]

Commands:

  loadsyms <vmname>|<uuid> <symfile> [delta] [module] [module address]
      This will instruct DBGF to load the given symbolfile
      during initialization.

  unloadsyms <vmname>|<uuid> <symfile>
      Removes <symfile> from the list of symbol files that
      should be loaded during DBF initialization.

  setvdiuuid <filepath>
       Assigns a new UUID to the given VDI file. This way, multiple copies
       of VDI containers can be registered.

WARNING: This is a development tool and shall only be used to analyse
         problems. It is completely unsupported and will change in
         incompatible ways without warning.

Syntax error: Invalid command 'createrawvmdk'
alex@scaleo-gg:~/vm$ 



Using sudo doens't help here.

---

### Post by P4man on 2007-11-07
I think you need the binary version of virtualbox for that. The OSE one has some limitations.

---

### Post by P4man on 2007-11-07
BTW, if your windows disk is mounted under linux, why not map it as a network drive to your VM ? Sounds safer (and easier) to me.

---

### Post by PokerJoker on 2007-11-07
> **P4man said:**
> BTW, if your windows disk is mounted under linux, why not map it as a network drive to your VM ? Sounds safer (and easier) to me.

Sounds good, need to look up how to do that though, i guess i need ntfs write support for it to work?

Edit: found your blog, nice one. mount -t vboxfs gives unknown filetype, guess i need to get the binary.

---

### Post by P4man on 2007-11-07
ntfs-3g is installed by default in gutsy, so you should already have write permission. And yeah, in the blog you can find help on it; I've submitted a how-to that elaborates more on the network drives, but it has yet to be published.  I suspect you will manage with the short info there though.

---

### Post by PokerJoker on 2007-11-07
> **P4man said:**
> ntfs-3g is installed by default in gutsy, so you should already have write permission. And yeah, in the blog you can find help on it; I've submitted a how-to that elaborates more on the network drives, but it has yet to be published.  I suspect you will manage with the short info there though.

True on both counts ;-)  Got to boot my recovery/install CD, just didn't finish it, as i don't have any more time tonight, also my vista ntfs partition is mounted an writebla by default, i just love Gutsy.....
Thanx for the input

Edit:  XP installed, Guest additions also. It's running like a dream. Now the wife can play The Sims without me having to reboot, killer......

---

