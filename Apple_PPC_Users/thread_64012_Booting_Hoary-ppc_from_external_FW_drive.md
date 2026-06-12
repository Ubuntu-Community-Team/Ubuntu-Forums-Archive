---
title: "Booting Hoary-ppc from external FW drive"
date: 2005-09-09
forum: Apple PPC Users
---

### Post by king_arthur on 2005-09-09
Hi there, I know that this has been done in several ways however, most of the times it's done via some tricky modification which I haven't been able to fully understand.

There is a a Wiki [here]("https://wiki.ubuntu.com/BootFromFirewireHardDisk") but it is taken over from a YDL setup and very inaccurate.
With YDL however, the trick seems to be long since possible, I found some extensive documentation [here]("http://131.204.27.45/ydl-howto/") but wasn't able to make it work in Hoary.

The Hoary installer hangs when writing the bootloader.

Alternatively, I have tried the Breezy installer which seems to have improved external HD support but that also hangs for ever when it comes to OS detection to be written into the configuration file (external HD).

What I really want is an external FW hard disk that can simply be plugged into any compatible Macintosh and from there boot into Ubuntu. 

Same as with the live CD.. hey.. that should be easy!!

I don't mind burning a startup CD but I don't want do modify my existing, internal, filesystem (OSX) or bootloader.

To the best of my knowledge, booting from external Linux media is possible but I don't have the Yaboot and OpenFirmware skills to setup the system by myself. 

Could anybody that has solved this problem pls help?

Eventually a good Wiki will be needed to solve this issue permanently.

/P

---

### Post by TroutMaskReplica on 2005-09-09
> Eventually a good Wiki will be needed to solve this issue permanently.

forget the wiki. the installer should be fixed or the PPC version should be pulled if it's not going to be maintained properly.

---

### Post by interrupt on 2005-09-13
I posted the essentials of booting from an external firewire disk 

[here](http://www.ubuntuforums.org/showthread.php?t=29837) 


Although there is a bug that prevents installing a new ubuntu system to the firewire disk, it is quite easy to create a bootable ubuntu on the firewire disk – providing you have a working ubuntu installation somewhere else (i used my iBook internal drive). 

As an alternative route, it ought to be possible to create the bootable firewire system with a live CD. I've not tried this, so am only speculating.

---

### Post by nulio on 2005-09-13
Hello !
Would it be possible to create an "iso" image of your "firewire installation" and make it available to the community. Then we only have to clone this "iso" to the external hard drive.

I am looking for an easy way to install ubuntu on an external hard drive...
Thanks

---

### Post by king_arthur on 2005-09-17
[QUOTE=interrupt]I posted the essentials of booting from an external firewire disk 

[here]("http://www.ubuntuforums.org/showthread.php?t=29837") 


Although there is a bug that prevents installing a new ubuntu system to the firewire disk, it is quite easy to create a bootable ubuntu on the firewire disk – providing you have a working ubuntu installation somewhere else (i used my iBook internal drive). 

As an alternative route, it ought to be possible to create the bootable firewire system with a live CD. I've not tried this, so am only speculating.[/QUOTE]

I had a go at ramdisk and initrd but, regretfully, I did not succed..

It is to say that I am no newbie to Linux but must admit I never fully understood the mechanism governing the boot process i.e. loading kernell and filesystem.
Thanks to your post and subsequent investigation, I do much better now however, I feel this stuff is well over my head.
The several sites and howto's read so far, agree on the basics but differ on the actual creation of the RAM image, for instance:
Typing $sudo mkinitrd returns a help screen showing several options.

If I use any of them such as -0 (output file) or -r (root filesystem) I am getting errors.

As I understood correctly, the **mkinitrd** command should be able to create a working Ram image of the kernel using the info contained in both, the running kernel, as well as the initrd.conf file.
How the devil can I get this done onto my external disk?????

Problem maybe is that I am trying to do this from the live CD and I can't find my way trough the existing directories.

Furthermore, the external FW drive filesystem is mounted in /media/ieee1394disk which differs from what other distros do, hence I am a bit lost.

I have also been monitoring the progress made on the ubuntu.bugzilla repositories, but it seems like the developers (i.e. cjwatson) are kept busy with other priorities and we will have to wait a long time for this to get fixed into the installer. Check [here]("https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=yaboot&field0-0-1=component&type0-0-1=substring&value0-0-1=yaboot&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=yaboot&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=yaboot").
I guess it won't be before 06/04, that is "Drapper Drake".

Hopefully, under the guide of some knowleadgeable people like you, we will be able to fix it ourselves before that date... :D

/P

---

### Post by interrupt on 2005-09-19
Hi,

Normally the -o and -r options to the mkinitrd command tell it where to create the image and what the current root device is. Can you post an example of your use of mkinitrd and the errors generated?

Once the image is made properly, you can just copy or move it – then you need to tell yaboot where it is with the initrd= line in your yaboot.conf file. I keep mine in the same place as the kernel image so in my yaboot.conf there are lines similar to:

image=/boot/vmlinux
initrd=/boot/nameofmyrdimage.img


I reckon trying to do this with the live CD is making everything more complicated for you. Is there no way you can install linux onto your internal drive? For example, clone OS X to a safe place then re-partition the internal drive to give enough free-space to install ubuntu onto.  Put OS X back and you'll have both operating systems bootable on the internal drive. Once you get linux booting from the firewire drive you can then give the whole internal back to OS X.

Plus, you'll then be working from the same situation I was in and I'll be able to show you step by step how it works.

---

### Post by interrupt on 2005-09-20
I'm going to post some of the configuration files I used, starting with my mkinitrd.conf. It looks pretty standard though.

Here it is:

```
# /etc/mkinitrd/mkinitrd.conf:
#  Configuration file for mkinitrd(8).  See mkinitrd.conf(5).
#
# This file is meant to be parsed as a shell script.

# What modules to install.
#MODULES=most
MODULES=none

# The length (in seconds) of the startup delay during which linuxrc may be
# interrupted.
DELAY=0

# If this is set to probe mkinitrd will try to figure out what's needed to
# mount the root file system.  This is equivalent to the old PROBE=on setting.
ROOT=probe

# This controls the permission of the resulting initrd image.
UMASK=022

# Command to generate the initrd image.
MKIMAGE='mkcramfs %s %s > /dev/null'

# Set this to yes if you want to use busybox(1).
BUSYBOX=no

# Set this to no if you want to disable /usr/share/initrd-tools/scripts.
PKGSCRIPTS=yes

# This is the value for LD_LIBRARY_PATH when deciding what goes onto the
# image.
INITRD_LD_LIBRARY_PATH=$LD_LIBRARY_PATH

```

---

### Post by interrupt on 2005-09-20
Then the modules file –*I compiled all the drivers I needed for firewire into my kernel so this doesn't do much.

 ```
# /etc/mkinitrd/modules: Kernel modules to load for initrd.
#
# This file should contain the names of kernel modules and their arguments
# (if any) that are needed to mount the root file system, one per line.
# Comments begin with a `#', and everything on the line after them are ignored.
#
# You must run mkinitrd(8) to effect this change.
#
# Examples:
#
#  ext2
#  wd io=0x300

```

---

### Post by interrupt on 2005-09-20
This is the important one – the linuxrc script. It gets my firewire root partition up then pivots to it.

```
#!/bin/sh
#
# $Id: linuxrc,v 1.11 2004/04/26 12:04:46 herbert Exp $
# this file is located at /usr/share/initrd-tools

mount -t proc /proc /proc

# loop rescanning SCSI bus

echo "scsi add-single-device 0 0 0 0" > /proc/scsi/scsi
sleep 1
echo "scsi add-single-device 0 0 0 0" > /proc/scsi/scsi
sleep 1

echo 0x805 > proc/sys/kernel/real-root-dev

umount /proc

exit 0

```

---

### Post by interrupt on 2005-09-20
This is just a listing of my /boot directory. It contains my kernel image and the initrd image and various links

```
total 14588
drwxr-xr-x    2 root     root         4096 2005-04-22 20:59 .
drwxr-xr-x   22 root     root         4096 2005-04-14 23:30 ..
-rw-r--r--    1 root     root        40674 2004-10-12 14:13 config-2.6.8.1-3-powerpc
lrwxr-xr-x    1 root     root           28 2005-04-14 23:24 initrd.img -> initrd.img-2.6.8.1-3-powerpc
-rw-r--r--    1 root     root      1396736 2005-04-25 21:08 initrd.img-2.6.8.1-3-powerpc
-rwxr-xr-x    1 root     root      5715347 2005-04-24 10:16 new_kernel
-rwxr-xr-x    1 root     root      5715347 2005-04-24 20:54 old_kernel
lrwxr-xr-x    1 root     root           10 2005-04-22 20:59 stable_kernel -> old_kernel
-rw-r--r--    1 root     root       940819 2004-10-12 14:37 System.map-2.6.8.1-3-powerpc
lrwxr-xr-x    1 root     root           10 2005-04-15 23:01 vmlinux -> new_kernel
-rw-r--r--    1 root     root      1281970 2004-10-12 14:37 vmlinux.coff-2.6.8.1-3-powerpc

```

---

### Post by interrupt on 2005-09-20
Finally, my yaboot.conf which shows how the bootloader is configured to enable a boot from firewire with root on /dev/sda5, via the initrd image located at /boot/initrd.img

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
timeout=100
install=/usr/lib/yaboot/yaboot
ofboot=/pci@f4000000/firewire@e/node@00d04b391d083ab2/sbp-2@c000/disk@0:
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
#macosx=/dev/hda10
fgcolor=light-green
defaultos=macosx

image=/boot/vmlinux
	label=Linux
	device=/pci@f4000000/ata-6@d/disk@0:
	partition=12
	root=/dev/hda12
	read-only
	append="quiet splash"

image=/boot/vmlinux
	label=External
	device=/pci@f4000000/firewire@e/node@00d04b391d083ab2/sbp-2@c000/disk@0:
	partition=5
	root=/dev/sda5
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/stable_kernel
	label=Stable
	partition=12
	root=/dev/hda12
	read-only
	append="quiet splash"

```

---

### Post by king_arthur on 2005-09-21
Hi Interrupt,

first of all, sorry for late reply and many thanks for making all your configuration files available. 
I will fully investigate what you did and try to tailor according to my setup.

Haven't been able to make much progress on this issue so far, will keep you posted.

What puzzles me is that this would be an extremely useful feature if fixed into the original installer however, there seem to be only a bunch of "pioneers" wanting to find a workaround for this bug which, IMHO, should have a fairly high priority with the ppc developers (Colin?) as it would make Ubuntu-PPC fully portable on a external HD...

We will see

Cheers

/P

---

### Post by king_arthur on 2005-09-23
Hi Interrupt,

I have been spending a few sleepless nights digging further into this matter but have been accumulating only frustration. :mad:

I decided to follow your suggestion and made one partition available on my internal HD to start with. I than proceeded installing on above partition the latest release of breezy-ppc which went on till completion uneventfully.

Sad as it is, after everything was finished, I couldn't log in as my usb keyboard apparently wasn't recognized. Unplugging and plugging back didn't help.

Probably still something with hotplugging that doesn't work as it should.

Back to the drawing board, I have taken a copy of the Hoary installer to do the same thing, this time the keyboard worked but many other things didn't as the installer didn't complete it's run and I had to manually complete installation hacking my way into several problems I found.

Now that I got a decent working system, I still can't mount the external FireWire HD. Perhaps fw support missing in the kernel?
I am starting to slowly get fed-up with all this crap as Tiger OSX is doing such a superb job on the same machine as well as the old PB WallStreet that I also have.

I am not giving up as, after 4 years on Linux I know quite well that by error and trial I will eventually succeed ](*,) but I certainly need a break before I get any further.

Strangely, the live-CD works extremely well, recognizes all the available h/w including Airport WiFi and WEP encryption and even allows using my external drive including hfs+ and ext3 partitions..
That's weird to say the least.:confused:

What's wrong here?

Cheers

/P

---

### Post by interrupt on 2005-09-27
Hi king_arthur,

Glad you've got a system going on the internal drive. That's pretty lame that the keyboard was not recognised with breezy install. I'm can never remember which version I have – think it's warty. I wish they would just refer to the different versions by number :?  I once also had no keyboard use but that was after messing around with the kernel – it shouldn't happen from an install. Not saying it's neccessarily the developers' fault but...

Right, first you have to get the firewire drive working with this system you've got on the internal drive. This is going to mean recompiling your kernel to include all the neccessary support for the device, either in the kernel itself, or via modules. I would compile support in rather than going the modules route because it will mean you don't have worry about modules when you do 'mkinitrd' later.

Good Luck! I get what you're saying about getting fed up with it – it took me months to sort it out. My wife wasn't too happy either ;)

Oh, the live–CD worked better because it's kernel is probably already configured for every conceivable bit of hardware. It'll be pretty bloated though and/or use loads of modules that you don't need.

---

