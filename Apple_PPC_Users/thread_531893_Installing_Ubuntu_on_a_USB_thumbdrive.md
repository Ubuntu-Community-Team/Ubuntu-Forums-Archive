---
title: "Installing Ubuntu on a USB thumbdrive"
date: 2007-08-22
forum: Apple PPC Users
---

### Post by iamdigitalman on 2007-08-22
so, I have this 2gb thumbdrive, and nothing to use it for. So, I plug it in to my 2001 iBook, and boot off of my ubuntu 6.06 alternate CD. It takes quite some time, but eventually, it's done installing, and it begins installing the bootloader. It gets to 83%, and says installation of the bootloader failed, and I may have an unbootable system. So, I pull out my old 5.10 shipits, and whip out the mac version. Pop it in, and begin installing. This time, it takes a lot less time. However, it fails in exactly the same spot. 83% of the bootloader.

Is there some extra step to getting it installed? I also assume I can update all the way to feisty.

my next step is to reboot this B&W G3, and attempt to install it on the thumbdrive with it. The B&W also has a USb 2.0 card, which should speed things up further.

-digital ;)

---

### Post by pxwpxw on 2007-08-22
The problem shared by ubuntu, debian and other distro yaboot installers is failure to get the correct yaboot installer paths for usb ( and some others devices).

You can put a copy of yaboot and yaboot.conf on your hard drive, and edit yaboot.conf to get the usb stick booted, and/or you can patch the ofpath utility used by the yaboot installer and then re-install the booloader on the usb stick, and (with luck) boot from that. 

Edit: This does not apply to (some?) usb external hard drives, which use a different interface, and won't boot directly even if the ofpath problem is fixed. Firewire external hard drives don't have that problem.
 
I have submitted a launchpad bug report with attached patch for ofpath that does the trick. I will add a link to that here.

ofpath failure -sata, firewire, usb - patch to fix

[https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607")

---

### Post by ajmctaggart on 2007-08-22
Two things:

1) Although I did not have the patience or knowledge AT THE TIME, it is well documented how to install yaboot by manually partitioning in Disk Utility, then moving the files necessary to the 1st small partition..

2) With some playing around, and a little googling' you can learn how to use the open firmware command to tell your computer where to boot from (i.e.- directing your iBook to usb1 partition1 file yaboot.conf (just an example, this is nothing even close to what the command would be)

So, Partition the Drive, install Ubuntu on the Second Partition on, and lets keep working on how to manually move yaboot over to part1 on your usb drive, I want to know how to do this too...

GOOD LUCK!

Thanks,
ajm

---

### Post by meccax5 on 2007-08-25
anyone solve this problem yet?

---

### Post by pxwpxw on 2007-08-25
Read my post above, that works.

---

### Post by meccax5 on 2007-08-25
yeah i am kind of a noob....can u elaborate?
lol. please?

---

### Post by pxwpxw on 2007-08-26
**meccax5**

This post assumed a USB flash thumb drive or stick. The problem is different for a usb external enclosre hard drive, see the later posts for  **meccax5** external usb.
======end of edit


Well, assuming you have a NewWorld Applemac ppc (i.e. a G5, G4, or late model G3).

There is a small but critical bug in the bootloader installer, that screws up the final install stage of setting up the boot loader (yaboot). Everything else is all there ready to go, it just cant boot without help.

This bug is easily fixed by a small patch to one small file (ofpath) which is part ot the yaboot installer package. 

If the bug was eliminated, the install from an Alternate Install CD, to a usb stick would be just a normal install, and would reboot ready to go after finishing the install. (some usb sticks have extra garbage and need to be avoided).

But the bug is not fixed (see my post above, with launcpad bug report link which also has a patch to fix the bug). 

So it has to be fixed either - 

(a) during the initial install, by getting and applying the patch to the ofpath file, before the installer finishes installing the boot loader. This a bit tricky and needs an expert install, but only requires a few command lines.
I did it this way, after a trial run.

(b) by letting the install finish with the bug, then running the installed system by booting temporarily, from the apple Open Firmware, or a rescue disk, then doing the same patch procedure and then installing the boot loader. This way is probably easier.

(c) manually correcting the yaboot.conf file and re-installing the boot loader.
Ok if you dont want to do the patch, but more work.

---

### Post by meccax5 on 2007-08-26
ok i decided to use the third option.

installed ubuntu and i mounted the linux drive on os x.

how do i edit yaboot?

---

### Post by pxwpxw on 2007-08-27
Before deciding which way to finish the job, we need more info.
It is /etcy/yaboot.conf we ned to see.

Where have you installed linux?
How have you mounted the linux partition in macosx?
Can you post a listing of the linux / files? In particular /boot and /etc/yaboot.conf
Post a copy of /etc/yaboot.conf.

What version MacosX have you?

Need to know all disk partitions, includig the usb.
From macosx teminal -
```

 diskutil list

```

You cannot write directly to linux from macosx (unless you have something that does that), will have to copy yaboot.conf to macosx, edit, caopy back from linux.

You will need  to boot back into ubuntu from open firmware when ready, but need the info above to do that.

---

### Post by meccax5 on 2007-08-27
1.Where have you installed linux?

/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *27.9 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:              Apple_HFS Macintosh HD       27.8 GB   disk0s3
/dev/disk2
   #:                   type name               size      identifier
   0: FDisk_partition_scheme                    *111.8 GB disk2
   1:              Apple_HFS WD Passport        40.5 GB   disk2s1
   2:                  Linux                    7.8 MB    disk2s5
   3:                  Linux UNTITLED           68.0 GB   disk2s6
   4:             Linux_Swap                    2.2 GB    disk2s7

2. How have you mounted the linux partition in macosx?

 i used [http://sourceforge.net/projects/ext2fsx](http://sourceforge.net/projects/ext2fsx).

Can you post a listing of the linux / files? In particular /boot and /etc/yaboot.conf

/boot = abi-2.6.20-15-powerpc, config-2.6.20-15-powerpc,initrd.img,initrd.img-2.6.20-15-powerpc, system.map-2.6.20-15-powerpc, vmlinux, vmlinux-2.6.20-15-powerpc

Post a copy of /etc/yaboot.conf.

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda5
partition=6
root=/dev/sda6
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

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


What version MacosX have you?
10.4.10


BTW, thanx for all the help.

---

### Post by pxwpxw on 2007-08-27
**meccax5**

Forgot to ask what mac is that.

Can you see what if any files are in the disk2s5 7.8 Mb, which corresponds to sda5 boot partition for the  linux install. It should be type Apple_Bootstrap if the installer did its full job.

Did the yaboot install give any errors or confirmation?

Also can you see if you can write to that boot partition from macosx  - would make things easier.

I thought you were using a usb flash stick, but that must be an external  usb enclosure, don't think that makes any difference, might make it easier, but need to get the boot partition sorted out.
That usually gets created by the partitioner. It should have given a warning if there was no boot partition 

And please do from macosx
```

 nvram boot-device
 nvram -p

```

save yourself a copy and post just the boot-device.

There was a very similar install recently, I will post a link when I find it.

---

### Post by meccax5 on 2007-08-27
it is an ibook g4.

i cannot see thefilesin the 7.8mb partition. it justsays format type is linux.

boot device gets:

 boot-device     pci2/ata-6@D/@0:3,\\:tbxi

i can't write to the partition.

and yeah its an external hard drive.

---

### Post by pxwpxw on 2007-08-27
Right, makes it a bit different, not so easy. I just checked out on an external usb here, it needs to boot the linux kernel off the internal hard drive - I wiil need a little time to check that out here, I have done it that way before, esentially you copy the kernel and initrd to the macosx (or other hfs+) partition together with yaboot and yaboot.conf, then boot through that to the linux root, with a yaboot menu to select linux or macosx. 

It is possible to check your external to see if it may be direct bootable from Open Firmware, could be different to mine. Do that with the "dir" command from open firmware, detail later.

The direct boot for a flash drive (stick) works differently, it is simpler. If you have an alternative firewire connection you can boot directly to the external, I have that here also.

I will try to get something for you tomorrow, bit late here now.

Edit:

I have an ibook g4 and usb external drive here, checking it out, should have something soon..

---

### Post by pxwpxw on 2007-08-28
**meccax5** for your external usb enclosure configuration as above.

Have a look at this.

This is how I do it initially with an iBookG4 and external usb 160GB
This kind of thing is easier if you have a minimal linux install and boot partition on the main internal drive, with Macosx (as I have), but the ext2fs utility on macosx should be very useful too.

To boot the external ubuntu installation on partition 6. (/dev/sda6)

```

1. copy 2 kernel files from linux /boot to Macintosh HD root.

initrd.img-2.6.20-15-powerpc
vmlinux-2.6.20-15-powerpc

rename them vmlinux and initrd.img

(links or aliases are no good)

2. Copy /usr/lib/yaboot/yaboot to Mac HD root 
 (or you can find it on the iso or CD)

3. Write yaboot.conf (template below) to M HD root

You now have in Mac HD root: 4files
 yaboot, yaboot.conf, 
 vmlinux,
 initrd.img,

4. Restart from Macosx into Open firmware. Command-Option-O-F 
  ( Command-Option-P-R at startup (2 chimes) resets boot-device to boot Macosx.
   the default boot-device is probably hd:,\\:tbxi )

In Open firmware:

0> dir hd:3,\
Shoudl list files in MacHD root at hda3, 
 yaboot yaboot.conf vmlinux initrd.img should be there.
If they are not, 3 may be the wrong partition number, try 2 or 4 etc/
(or they may not be in the root of the partiton)  

0> dir hd:3,\yaboot
This step is not really needed,
Should return "Can't DIR a file, DIR method failed" - just confirms it can find files.

0> boot hd:3,yaboot
Should boot yaboot menu then the linux kernel.

0> shut-down
If it fails

0> devalias 
 lists all the open firmware aliases (short names)
0> dir usb0/disk:0,\
0> dir usb1/disk:2,\
examples which should show a list if you hit the drive and a partition that is bootable 
from open firmware (unlikely since you have  a Fdisk Partitioning scheme).
Otherwise they hang for a minute or so and error message.

$ sudo lshw -v
 gives good info about the external usb drive.

```
==================
5. yaboot.conf - template - check carefully for your configuration.
This is the complete yaboot.conf file to use for this stage, nothing more should be added.

```

### boot external usb root at sda6 from macosx at hda3

image=/vmlinux
	label=usb
	initrd=/initrd.img
	root=/dev/sda6
device=hd:
partition=3

image=halt
	label=A


```
======

Initially use the option key startup to boot macosx, and set the boot device to boot yaboot as above.

When you have ubuntu running from the external drive, then create from there a proper boot partition (man mac-fdisk hfsutils and ybin) on a small partition on the internal drive, which will give menu options for macosx, linux, and anything eles you want. 

If you have it on macosx, pdisk will show where the free spaces are:

```

 sudo pdisk -l

```

You will still need to boot the kernel from the hard drive, unless your external usb enclosure is better than mine. (Not so for a usb flash stick if properly formatted and installed.). If it looks like more problems, consider reinstalling (not the same way), with an Apple_Bootstrap boot partition and kernel on the main drive, use the Alternate install CD, not the Desktop CD.

If you upgrade or change kernels, you need to do the same to the copies on the main drive,
======

---

### Post by meccax5 on 2007-08-28
thanx alot. i am gonna try it out a little later and get back to if it works.

---

### Post by meccax5 on 2007-08-28
ok open firmware wouldn't let me dir to yaboot

and also can u make sure my yaboot.conf is right.


## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=hda3
partition=3
root=/dev/sda6
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

image=/vmlinux
	label=usb
	read-only
	initrd=initrd.img
	append="quiet splash video=ofonly"

image=halt
	label=halt
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash video=ofonly"

---

### Post by pxwpxw on 2007-08-29
**meccax5**

I have edited the howto to clarify about dir and yaboot.conf.

See  the edited howto about trying other partitions from open firmware.
Your yaboot.conf is not the one we want here, and it has errors, trash it.
The mini yaboot.conf is just to get your installed system booted..

Create a new yaboot.conf with only the text below, nothing added.
It is correct for macos hd at  hda3 and the external ubuntu root at sda6.
The comments about checking were more for other readers, and in case I had got something wrong.


```

image=/vmlinux
	label=usb
	initrd=/initrd.img
	root=/dev/sda6
device=hd:
partition=3

image=halt
	label=A

```

---

### Post by meccax5 on 2007-08-29
yeah i dunno i can't get it to work. 

thanx for ur help tho.

---

### Post by pxwpxw on 2007-08-30
Sorry you can't make it work.

Did you try     boot hd:3,yaboot   
 what happended?

Only takes one typo to make it fail.

---

### Post by Gen2ly on 2008-02-18
Appreciate all the awesome information pwxpwx!  I had time this weekend to try this out.  It looks like, however, that some versions of Open Firmware won't recognize usb disks.  :( :( :(
 
Anyways, I did research this a bit so I decided put pen to paper since I couldn't find any guides on this about.  

Please be free to correct any errors I may have made.

[Link Link]("http://gentoo-wiki.com/LiveUSB_on_PPC")

---

