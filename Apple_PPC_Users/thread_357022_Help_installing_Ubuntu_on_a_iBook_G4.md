---
title: "Help installing Ubuntu on a iBook G4"
date: 2007-02-09
forum: Apple PPC Users
---

### Post by steve-0 on 2007-02-09
hello everyone!

first of all, i want to excuse myself for my english (i'm spanish)...

well, couple days a go i bought an iBook G4 and i want to install Mac OS X in a 24GB partition and the rest for Ubuntu (i just need it for university....) so 1GB swap and 3GB ext3, but i just can't...

i tryed to install first MAC os X and when I try to install Ubuntu i can click to the last 'acept' before installing cause it says that there's a NewWorld partition missing..

and also tryed installing first Ubuntu, afterwards MAC but now i can't boot Ubutnu, it just boots Mac...

yesterday i was googling the whole evening and i can't find any 'how to...'

ani tip?

--EDIT--

and also, i don't need much perfomance in ubuntu, it would be only for programming and stuff like that... if i have to reinstall MAC OS X, could i just install any virtual machine on MAC OS X to install Ubuntu?

thank you very much..!

---

### Post by grazie on 2007-02-09
It sounds like you are trying to create the Ubuntu partitions yourself, but are not doing it quite right. Also, if you've only got 4G of space available for Ubuntu, using a 1G for swap is rather a lot. I'd suggest deleting the partitions you created for Ubuntu and leaving them as free space (you don't have to re-install OS X). Then from the installer select the option where Ubuntu creates the partitions from the lagest available free space.

Also, the documenatiion says to use the alternate CD if you've got 128M of RAM or less. In practice I'd still use the alternate CD if you've got less than 256M of RAM.

Virtualizition software for PPC is not well supported. You could instal MOL (Mac On Linux) on Ubuntu to run MacOS and MacOS X, but you'd be best to re-work your partitions completely, Also you'd need at least 512M of RAM, preferably more. Dual booting is the much better option.

---

### Post by Kalvin on 2007-02-09
steve-o:

You'll definitely need to use the Alternate CD to set up your dual-boot.  The message you got from the installer on the Desktop CD says you need a NewWorld Boot Partition.  Unfortunately, this is not something that can be created using the Desktop CD.  This option is only available using the partitioner used for the text-based install on the Alternate CD.

Order of operations:
1)  Install OS X first (or as grazie notes below, just delete the ubuntu partitions).  Before you commit to the install, partition the Hard Disk into two parts:  24 GBs (or whatever you need for OSX) as MacOS Extended, and then the rest as Free Space.  Install OSX as usual.

2)  Boot to the Ubuntu Alternate Install CD.  Go through the text based installer until you get to where it asks where to to install Ubuntu.  Select "Manually Edit the Partition Table."

You actually need 3 partitions (I created them in this order):
a) NewWorld Boot Partion, it doesn't need to be very big...I used 8.5MB.  The partition type is "newworld" from the dropdown menu.  This needs to be bootable.
b) Swap partition
c) Ext3 partition which will mount as '/' ...leave a little space at the end of the drive (a few megs).  It may be just voodoo and not really necessary but that's what I do and it works for me -- I read somewhere that the apple boot process needed this.  (Since this is a little out of Snopes' scope, someone here can feel free to debunk this.)

Finish the install and you should be good to go.  Don't worry about the text installer, it's every bit as easy as the graphical installer.

I've never tried using the Automatic method using existing free space, that may create the newworld partition on its own.

---

### Post by grazie on 2007-02-09
Actually, both the Desktop and Alternate CDs are quite capable of creating NewWorld boot partitions, whether done automatically or manually. The only reason to choose either the Desktop or Alternate depends on the amount of RAM your machine has. No point in doing another download if you've got enough RAM.

---

### Post by Kalvin on 2007-02-09
Huh.  Didn't know.  Where is the option on the graphical installer to select NewWorld Partition?  When I've tried to set it up in the partitioner there is no option?

---

### Post by grazie on 2007-02-09
Kalvin,

I've never actually needed to create a NewWorld partition when I've installed *Ununtu, because there's always been one there already. However, if the Desktop CD couldn't do this their would be a whole load of very unhappy Mac/PPC owners out there, that couldn't boot there machines :). I'm doing a bit of testing in the next few days, so I'll see if I find it (probably not that obvious) in case so you can't find it yourself.

---

### Post by steve-0 on 2007-02-09
hello!

thank you very much for your answers... :)

i have 512MB of ram..

now i dont have the ubuntu dvd with me, but as soon as i get home i,ll try to delete swap and ext3 partitions and try to install it using the "free space left" option (or similar)

do you think that'd work?

also, one question more, installing ubuntu now (i have already mac os x installed) would grub be installed also? i mean, when i boot, i will be able to choose, right?

thank you again!

---

### Post by grazie on 2007-02-09
The plan sounds good to me. PPC machines like yours use yaboot which is the equivalent of grub, but not quite as user friendly. After you boot the machine you'll get options something like

l - linux
x - mac os x
c - cd

If you select l, you'll get to the linux boot screen. Just hit enter or to get the options hit tab and type in the option you want or again just hit enter.

---

### Post by steve-0 on 2007-02-10
it worked! :D

just one more question, if i don't press anything it does just what you said.. how can i do to if don't press any key, to boot MAC OS X?

---

### Post by grazie on 2007-02-10
Ahem, the x key? :)

---

### Post by pxwpxw on 2007-02-10
When ubuntu is installed after macosx, it finds macosx and writes /etc/yaboot.conf, and runs mkofboot
to install yaboot and other files on the Apple_Bootstrap (New world) boot partition.
Then after ubuntu is up and running you can edit yaboot.conf to
change first stage boot menu defaultos from Linux (l) to macosx (x).
 This example is is from my ibook g4, example only, dont use it.

It is for yaboot on /dev/hda2, macosx on /dev/hda3 (open firmware path hd:3)
and ubuntu / on /dev/hda5
your installation is probably different.

Dont change anything until you read the man pages for yaboot.conf ybin and
associated pages.
 
/etc/yaboot.conf:

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hda3

###
### next 2 lines I added to make first stage boot menu default to maacosx (x)
### requires run ybin again. see man yaboot.conf, ybin.
macosx=hd:3
defaultos=macosx
###

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=5
root=/dev/hda5
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

============
Then you need to run ybin to update the first stage boot menu.

ubuntu:~$ sudo ybin -v
ybin: Finding OpenFirmware device path to `/dev/hda2'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/hda2...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/hda2...
ybin: Installing /etc/yaboot.conf onto /dev/hda2...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/hda2 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
ubuntu:~$

Be careful.

---

### Post by steve-0 on 2007-02-11
thanks!! :D

---

