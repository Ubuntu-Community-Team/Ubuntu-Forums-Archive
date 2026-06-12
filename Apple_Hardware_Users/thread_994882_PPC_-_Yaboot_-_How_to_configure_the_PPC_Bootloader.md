---
title: "PPC - Yaboot - How to configure the PPC Bootloader - Multibooting"
date: 2008-11-27
forum: Apple Hardware Users
---

### Post by tiresia on 2008-11-27
This is a short how to, in order to understand how to fix your boot problems.

[COLOR="Red"]**1.**[/COLOR] **ofpath** is a utility to determine the OpenFirmware path of a device. If you want to know the OpenFirmware path of a device, e.g. /dev/sda3, just run ```
ofpath /dev/sda3
```


[COLOR="red"]**2.**[/COLOR] **A minimal PPC-Linux Partition Table** (without any MacOS) on /dev/sda looks like this 
```
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap bootstrap               1600 @ 64        (800.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 myLinux               85852160 @ 1664      ( 40.9G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                 8000820 @ 202238668 (  3.8G)  Linux swap
```
You can edit a partition table in Linux with **mac-fdisk**
Yaboot is on the second partition, the **Bootstrap Partition**. *Do not mount it!*


[COLOR="red"]**3.**[/COLOR] There are three ways to install yaboot on a Apple_Bootstrap Partition:
**ybin**
ybin is the bootloader installer for PowerPC based machines
ybin installs the bootloader according to the parameters in /etc/yaboot.conf
ybin uses ofpath to find the path to the bootstrap partition and to any defined macos/macosx partitions. 
**mkofboot**
is a symlink to ybin, with the difference that initializes the bootstrap partition prior to running ybin to install the bootloader on it
**yabootconfig**
Yabootconfig creates a default configuration file and then runs mkofboot to complete the bootloader installation

[COLOR="red"]**4.**[/COLOR] **The yaboot-configuration-file** 
A simple **/etc/yaboot.conf** in a dual-boot system with Linux and MacOSX looks like this
```
boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old

```
boot= the bootstrap partition 
device= openfirmware path to the root partition
partition= number of the root partition
root= the device name of the root partition

timeout= Sets a timeout in seconds for keyboard input. If no key is pressed for the specified time, the first image is automatically booted.
enablecdboot
macosx= device name of the MacOSX partition

There are more interesting options (for a complete list see 'man yaboot.conf') such as
macos= device name of the MacOS9 partition
password= to specify a password for starting the system
defaultos= to specify from wich os the computer starts
enableofboot
enablenetboot


*After any changes of the yaboot.conf file, in order to make yaboot aware of the new 'situation', you need to run always *```
sudo ybin -v
```

[COLOR="red"]**5.**[/COLOR] **MULTIBOOTING**
For any other Linux-OS you install, the yaboot installer specifies in the yaboot.conf file following parameters:
```
image=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/vmlinux
    label=sda4-Linux
    root=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:4
    append="root=/dev/sda4 ro quiet splash"
    initrd=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/initrd.img

```
image= the openfirmware path to the kernel-image (or to its symlink) 
label= the name of the Linux kernel to display at the second yaboot prompt  
root= the openfirmware path to the root partition
append= any options to pass to the kernel before starting
initrd= the openfirmware path to initrd

When you start the computer, at the yaboot prompt, you can choose which OS you want to boot from (Linux, MacOSX, MacOS) or if you want to boot from a CD (if in yaboot.conf there is the option enablecdboot). After you choose to start from Linux, if you hit TAB, you will find a list of the different Linux-Kernels for each installed Linux Distro. With the option 'label' in the list above, you can specify the name for each of them.

*Usually you do not need to configure your yaboot.conf file*. But it can happens, that the Linux Installer fails to detect other Linux Distros installed on the computer (for me, by installing Fedora 10, the installer did not detect my Debian and Ubuntu partitions).
Since I never had a problem with the Debian Installer, if I want to install different Linux Distros, I run Debian *after* the Installation of the others - it detectes the other MacOS or LinuxOS's always correctly.


[COLOR="red"]**6.**[/COLOR] **In Ubuntu Hardy (8.04) ofpath fails to detect the correct openfirmware path in some PowerMac g5**
The problems for some PowerMac G5 come from the ofpath utility, because it fails sometimes to find the right openfirmware path (sometimes, not always: on my PowerMac G5 it works well). 
Even if you set in the /etc/yaboot.conf the right Open Firmware path, yaboot will not work correctly, because ybin and mkofboot need to run again ofpath (that is buggy)

**SOLUTION**
There is a fix for the ofpath, that you can download here:
[https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607)
(It was fixed in Ubuntu Intrepid 8.10 - *thanks to PeterXw!*)

If you download the ofpath.gz on your Desktop run
```
zcat Desktop/ofpath.gz > Desktop/ofpath
```
To overwrite the buggy utility with the fixed one just
```
sudo cp Desktop/ofpath /usr/sbin/ofpath
```
Now you can test if you get the right Open Firmware Path 
```
ofpath /dev/sda2
```
You can now just run
```
sudo yabootconfig -b /dev/sda2 -r /dev/sda3
```
The -b option specifies where the bootloader is, the -r option is the 'root' device.
Change the bootloader and the root devices according to your Partition Map (actually you shouldn't need to specify the root device)
Say yes, when you are asked, if you want to run mkofboot


·······
**USEFUL LINK**
[http://www.alaska.net/~erbenson/](http://www.alaska.net/~erbenson/)

·······
I hope I was quite clear (sorry, but english is not my first language). Feel free to suggest any corrections.

---

### Post by pxwpxw on 2008-11-27
I updated the launchpad entry with the ofpath.gz (previous attachment was full text script)

I think it will need chmod +x to make executable ofpath.

The Intrepid version yaboot package with the fixed ofpath is
$ dpkg -l yaboot
  yaboot       1.3.13a-1ubuntu5    Yet Another Bootloader

Attached is yet another gzipped copy of that ofpath.

---

### Post by mfox on 2008-11-28
Very useful information, tiresia; thanks for posting this.  I discovered on my own that not every distro does a proper job of configuring the yaboot menu, but Ubuntu and Debian do.  Here's a question - what is /dev/sda1?

---

### Post by tiresia on 2008-11-28
In my example /dev/sda1 is the Apple Partition Map.
Here some informations:
[http://en.wikipedia.org/wiki/Apple_Partition_Map](http://en.wikipedia.org/wiki/Apple_Partition_Map)
[http://developer.apple.com/technotes/tn2006/tn2166.html](http://developer.apple.com/technotes/tn2006/tn2166.html)

---

### Post by concorde106 on 2008-11-28
Man, if only I found this when I was still dual-booting my PowerBook G4... If I reinstall Ubuntu I'll use it! Thanks! Although, isn't sda for Macintel, and hda powerpc? My AlBook G4's partitions are called hda...

---

### Post by tiresia on 2008-11-28
> **concorde106 said:**
>  Although, isn't sda for Macintel, and hda powerpc? My AlBook G4's partitions are called hda...

No, **s**da (sdb,sdc, ...) refers to SCSI, Serial-ATA and USB Devices, while **h**da (**h**db, **h**dc, ...) refers to IDE Devices. For a FloppyDisk you have /dev/fd.

In your PowerBook g4 you have IDE-Disks, therefore your device is /dev/hda

[http://en.wikipedia.org/wiki/Device_file_system#Naming_conventions](http://en.wikipedia.org/wiki/Device_file_system#Naming_conventions)

---

### Post by MemphisJones on 2008-12-18
I have a dual boot iBook G3 with Hardy one hda3 and Intrepid on hda4.  I would like for Intrepid to be the default partition, so do I just add to my yaboot.conf file "default=hda4-Linux"?  Secondly, I installed Hardy after Intrepid on hda3 and its yaboot.conf file makes note of the hda4 partion, to add my default option to the file do I add it to the yaboot.conf located on hda3, or does it matter?  Lastly, i prefer the Hardy splash screen to Intrepid bc in Intrepid the colors are all wonky but they are fine in Hardy (the correct orange/red/yellow logo with orange progress bar).  Is it possible to somehow copy the Hardy splash screen to the Intrepid partion? What file should I look for and what all involves in changing that? Sorry for all the questions.

---

### Post by tiresia on 2008-12-19
> **MemphisJones said:**
> I have a dual boot iBook G3 with Hardy one hda3 and Intrepid on hda4.  I would like for Intrepid to be the default partition, so do I just add to my yaboot.conf file "default=hda4-Linux"?  
Secondly, I installed Hardy after Intrepid on hda3 and its yaboot.conf file makes note of the hda4 partion, to add my default option to the file do I add it to the yaboot.conf located on hda3, or does it matter?  

First of all: backup you yaboot.conf```
sudo cp /etc/yaboot.conf /etc/yaboot.conf.bak
```

The file /etc/yaboot.conf is not a configuration file for yaboot but for ybin. According to the parameters in that file, ybin installs yaboot on /dev/hda2. Therefore doesn't really matter, if /etc/yaboot.conf is on /dev/hda3 or /dev/hda4

The option 'defaultos=' (please, notice it's default**os** not default) is usually used to specify an OS other that Linux (macos, macosx, bsd). If it is not specified yaboot will boot a Linux Kernel (after a time delay as in timeout). 
At the second step, if you hit TAB, yaboot lists the names of the Linux Kernel on your computer, the first being the 'default' Kernel on the partition shown in 'partition='

Anyway, in your case, if you add 'defaultos=sda4-linux', it won't work, becaus 'sda4-Linux' is just a label, a name for the Linux Kernel, it is not the partition nor the root of that Kernel.

The easiest solution for you is just to boot in Intrepid (/dev/hda4) and run ```
sudo yabootconfig
``` It will set Intrepid as first Linux System to boot. If you want to edit yourself your yaboot.conf just as exercise, post it here and we can do it together.


> Lastly, i prefer the Hardy splash screen to Intrepid bc in Intrepid the colors are all wonky but they are fine in Hardy (the correct orange/red/yellow logo with orange progress bar).  Is it possible to somehow copy the Hardy splash screen to the Intrepid partion? What file should I look for and what all involves in changing that? Sorry for all the questions.
You can have a look here to get more information about 'usplash'
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by MemphisJones on 2008-12-19
I actually got kind of ansy last night and tried on my own after reading "man yaboot.conf".  Thank you for explaining the relationship bt ybin and yaboot, I didn't know that exactly.  I edited the yaboot.conf file on my partion number 3 (hda3) just bc it comes before hda4.  And like you suggested I made a copy of my file before I started editing.  Anyways I added "default=hda4-Linux" and that worked:)  I did not need to use "defaultos" bc I only have Linux on this box.  I will add my conf file, but I have to boot into the other partion to get it.  Thanks for the links on the usplash; I haven't figured that out yet but hopefully those links will head me in the right direction (i haven't read them yet).

---

### Post by MemphisJones on 2008-12-19
Here's my yaboot.conf file.  The only thing I changed was the "default=hda4-Linux".  So from what you are saying about ybin I could put this in my hda4 partition and and it would work.  Does it matter that this file has the added bit about "# This entry automatically added..." at the bottom?

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
default=hda4-Linux
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/hda4.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:4,/boot/vmlinux
    label=hda4-Linux
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:4
    append="root=/dev/hda4 ro quiet splash video=ofonly"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:4,/boot/initrd.img

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/hda4.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:4,/boot/vmlinux.old
    label=hda4-old
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:4
    append="root=/dev/hda4 ro quiet splash video=ofonly"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:4,/boot/initrd.img.old
```

---

### Post by tiresia on 2008-12-19
> **MemphisJones said:**
> Here's my yaboot.conf file.  The only thing I changed was the "default=hda4-Linux".  So from what you are saying about ybin I could put this in my hda4 partition and and it would work.  Does it matter that this file has the added bit about "# This entry automatically added..." at the bottom? 

You don't need to put this file in /dev/hda4/boot. When you run ybin, it will configure correctly the yaboot on /dev/hda2, regardless if you are running it on /hda3 or /hda4.

Ok, it can be that default=sda4-Linux works - so, if for you is ok you don't need to change it, but a much more canonical form would be like this
(BOLD is what I changed). 

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=**4**
root=/dev/hda**4**
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/hda**3**.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:**3**,/boot/vmlinux
    label=hda**3**-Linux
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:**3**
    append="root=/dev/hda**3** ro quiet splash video=ofonly"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:**3**,/boot/initrd.img

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/hda**3**.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:**3**,/boot/vmlinux.old
    label=hda**3**-old
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:**3**
    append="root=/dev/hda**3** ro quiet splash video=ofonly"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:**3**,/boot/initrd.img.old
```
Here you don't need to give the option for the default OS
Don't forget to run ```
sudo ybin -v
``` everytime you edit yaboot.conf

---

### Post by Farinet on 2010-11-22
Hi! I found this thread in search of help for a related problem:

On a PBG4 on the internal hd i've running Ubuntu 10.04. Now i installed on an external firewire hd mintppc. But something in defining the yaboot.conf file failed. Although Ubuntu is still running fine i cannot boot in mintppc. How could i manually edit yaboot.conf to be prompted on boot for a choice?

The structure of the both hds is this:

Internal (Ubuntu):
/dev/hda1     filesystem: unknown
/dev/hda2     filesystem: hfs 
/dev/hda3     filesystem: ext4            mountpoint:  /
/dev/hda4     filesystem: linux-swap

External (Mint):
/dev/sda1     filesystem: unknown
/dev/sda2     filesystem: hfs
/dev/sda3     filesystem: ext3            mountpoint: /
/dev/sda4     filesystem: linux-swap

The yaboot.conf (on hda3/etc/) looks like this:

> ## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ


boot = /dev/hda2
#boot = "/dev/disk/by-label/bootstrap"

device=/pci@f4000000/ata-6@d/disk@0:
partition=3

root = /dev/hda3
#root = "UUID=c7a26c93-8e02-4b6a-af14-64aea2493da9"

timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
    label=2635
    read-only
    initrd=/boot/initrd.img
    append="quiet splash"

image=/boot/vmlinux-2.6.34-ppcnux
    label=2634
    read-only
    initrd=/boot/initrd.img-2.6.34-ppcnux
    append="nosplash"I'm not sure, where and how to put in the lines referring to the external disks (from which using ofpath i got the labels (this, i presume: /dev/sda1 is: /pci@f4000000/firewire@e/node@0001a300000586c7/sbp-2@4000/disk@0:1)

Thanks in advance for any help!

PS. Eventually, there is an option to boot directly to the external firewire?

---

### Post by shawnhcorey on 2010-11-22
> **Farinet said:**
> Internal (Ubuntu):
/dev/hda1     filesystem: unknown
/dev/hda2     filesystem: hfs 
/dev/hda3     filesystem: ext4            mountpoint:  /
/dev/hda4     filesystem: linux-swap

External (Mint):
/dev/sda1     filesystem: unknown
/dev/sda2     filesystem: hfs
/dev/sda3     filesystem: ext3            mountpoint: /
/dev/sda4     filesystem: linux-swap


The first partition is the partition table.  It must be the first partition on the device.  You can look at it with:
```
sudo mac-fdisk -l
```

You can also change it with mac-fdisk but it's easier to use a partitioning application.

> **Farinet said:**
> PS. Eventually, there is an option to boot directly to the external firewire?

As far as I know, the only way to boot from any device but the hard disk or the CD, is to go through OpenFirmware.  Here's how to [boot from a USB drive]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware").

---

### Post by Farinet on 2010-11-22
Thanks for your reply. In the meantime i figured out what to do. My yaboot.conf now looks like this:

> ## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ


boot = /dev/hda2
#boot = "/dev/disk/by-label/bootstrap"

device=/pci@f4000000/ata-6@d/disk@0:
partition=3

root = /dev/hda3
#root = "UUID=c7a26c93-8e02-4b6a-af14-64aea2493da9"

timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot 

image=/boot/vmlinux
    label=2635
    read-only
    initrd=/boot/initrd.img
    append="quiet splash"

image=/pci@f4000000/firewire@e/node@0001a300000586c7/sbp-2@4000/disk@0:3,/boot/vmlinux
    label=mintppc9
    root=/pci@f4000000/firewire@e/node@0001a300000586c7/sbp-2@4000/disk@0:3
    initrd=/pci@f4000000/firewire@e/node@0001a300000586c7/sbp-2@4000/disk@0:3,/boot/initrd.img
append="quiet splash"

image=/boot/vmlinux-2.6.34-ppcnux
    label=2634
    read-only
    initrd=/boot/initrd.img-2.6.34-ppcnux
    append="nosplash"Moreover doing some bricolage on the bootstrap partition on the external hd (/des/sda), practically first i did an ybin -b /dev/sda2 from the internal hd (/dev/hda) and then manually i edited the yaboot.conf on ssda2 in a way it was identical to that in /dev/sda3/etc i managed that i can also use - during the Mac power on sound - the classical Mac option key to have the choice between booting from the internal or the external hd.

---

### Post by jharris1993 on 2012-02-01
Here's an odd one for you.

It appears that the folks who wrote yaboot never anticipated someone wanting to triple-boot between TWO OS-X installs and a Linux install.

Here is how my hard drive is set up:  (as shown by gparted)

Partition #1 - /dev/hda1 "unknown" locked partition (with a big red exclamation point!)
Partition #2 - /dev/hda2  Yaboot "New World" partition (16 meg)  Flag: boot
Partition #3 - "unallocated"  (128 megs)
Partition #4 - /dev//hda4  HPFS+ partition, labeled "New Tiger" (17.88 gig)
Partition #5 - "unallocated"  (128 megs)
Partition #6 - /dev/hda6  HPFS+ partition, labeled "Old Tiger"  (17.88 gig)
Partition #7 - /dev/hda7  HPFS+ partition, labeled "Boot OSX"  (8.5 meg)  Flag: boot
Partition #8 - /dev/hda8  ext4 partition for Xbuntu  (36.51 gig)
Partition #9 - /dev/hda9  HPFS+ partition, labeled "Boot OSX"  (8.5 meg)  Flag: boot
Partition #10 - /dev/hda10  Linux Swap partition  (1.99 gig)  Flag: swap

When I created the partition table using Mac's Disk Utility, I created five partitions: the partitions that ultimately became partitions 2, 4, 6, 8, and 10 as the only five partitions - all the others were added "behind the scenes" as it were, by the Mac.

I would like to set up yaboot such that when I get the boot menu, I get to choose between either one of the two OS-X partitions, OR the Xbuntu partition.
Viz.:  (something like this)
L - Linux
X - (first OSX partition) - can I set these labels to something useful?
Y - (second OSX partition)
C - CD-ROM

I chose the letters "X" and "Y" as arbitrary letters, they could be anything needed.

So far, the only information I have found is for:

[LIST]
[*]Booting between one Mac partition and one Linux partition
[*]Booting between one Mac-9 partition, one Mac-X partition, and one Linux partition.
[*]Booting between one or two Mac partitions (9 and X) and more than one Linux partition (by using "image=" statements.)
[/LIST]
What I want to find is how to boot between two or more Mac-X partitions, and a Linux partition.

I cannot believe that the folks at yaboot never considered the idea of using more than one Mac-X partition as part of the boot process - in the same way they allow more than one Linux partition.

I did try editing the yaboot.conf file to include **TWO** "macosx=" statements, one pointing to /dev/hda4 and the other to /dev/hda6.  What happens is that the first one encountered is the one captured.  The second "macosx" statement is ignored.

Any suggestions would be gratefully appreciated.

p.s.  Does anyone know how to make the yaboot menu a larger text size?  Right now on my system the entire yaboot menu takes up about a 2" x 2" square in the upper left hand corner - and is virtually impossible to read without a magnifying glass.

Jim (JR)

---

### Post by rsavage on 2012-02-01
Hi Jim,
 
As you say you can boot separately Mac OS and Mac OS X.  I don't know anything about Mac OS (or X), but I'm wondering if a possible quick fix for you would be just to pretend one of your Mac OS X partitions was Mac OS 9?
macosx=
macos=
 
I don't think the code for yaboot would be that complex.  It would be probably quite easy to hack something to produce a menu that was exactly to your specifications.
 
Can you not select the OS of your choice by holding down Alt/Option on startup?

---

