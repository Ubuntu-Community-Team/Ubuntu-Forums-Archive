---
title: "yaboot external booting"
date: 2007-09-28
forum: Apple PPC Users
---

### Post by pxwpxw on 2007-09-28
Booting direct from yaboot on the internal drive can get your external linux system restarted when there has been a problem with the yaboot bootloader installer at the end of the ubuntu install. Booting from yaboot skips the first stage (ofboot) of the full bootloader and the startup options are limited but usable. 
However. it will allow the external system to be run and from there the yaboot installer can be re-run to get full startup options.

I ran a test on my G5 to boot external enclosure hdd, xubuntu704 by usb or firewire, just using yaboot.

1. These are the boot files in the Macosx partition in folder /yatest
The kernel copies are just for convenience.
=================================
```

$ ls -l /yatest/ 
   153124 Jun  7 23:19 yaboot
      593 Sep 28 18:03 yaboot.conf
  7994585 Apr 21 14:46 initrd.img-2.6.20-15-powerpc64-smp
  7994585 Apr 21 14:46 initrd.img-copy
  8156208 Apr 15 06:54 vmlinux-2.6.20-15-powerpc64-smp
  8156208 Apr 15 06:54 vmlinux-copy

```
==================================

2. This is yaboot.conf

The yaboot menu will not appear if auto-boot? is true. (the default) So yaboot.conf needs the timeout entry.

I have edited this example for a single internal drive. It is not running, do not use without changing where needed, for your system.
```

## test yaboot.conf- booting yaboot for external linux root system
## usb or firewire
## yaboot and local kernel in Macosx partition /dev/sda3/yatest/ 
## linux root system in External hdd /dev/sdb6/ 

timeout=10
default=usb

#######################
# this usb image works for both usb and firewire
#
image=/yatest/vmlinux-copy
label=usb
root=/dev/sdb6
read-only
initrd=/yatest/initrd.img-copy
device=sd0:
partition=3

########################
# this firewire image uses the kernel on th external
# with firewire device path
#
image=/boot/vmlinux
label=fwr
root=/dev/sdb6
read-only
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=6

####end yaboot.conf#####################

```
3. Preparation to boot.

```


 Note the original boot-device for resetting.

$ nvram boot-device
boot-device     hd:,\\:tbxi

 Set boot-device for yaboot

If Macosx partition is at /dev/hda3

$ sudo nvram "boot-device=hd:3,\yatest\yaboot"
$ nvram boot-device
boot-device     hd:3,\yatest\yaboot


 The yaboot menu will not appear if Open Firmware auto-boot? is true.

$ nvram auto-boot?


```

4. Then restart the computer to boot yaboot.
===========================

Notes:

1. If auto-boot? is true, the Option key will get a macosx icon, with a delay about 1 minute for my g5, macosx can boot from that.

When booting from yaboot this way, IT WILL NOT DEFAULT TO MACOSX if the external boot fails (requires shutdown-Option key-restart).

If auto-boot? is false, the yaboot menu will appear. but yaboot cannot be used to boot macosx.

2. A separate Apple_Bootstrap hfs partition and full yaboot instllation on the internal drive will allow normal boot selection by the Apple Option key graphical picker (Apple Picker), or the ofboot/yaboot text menu. A small linux install on the internal drive is probably the easiest way to get this. 

============================

---

### Post by prestosd on 2007-09-28
Hey, just found out that if you switch the line to ```
default=macosx
``` it should boot Mac OS X! :)

---

### Post by cheezle on 2007-09-28
Ooh, thanks!  I've been considering getting an external hard drive to mess around with linux on rather than partition my internal drive.

Would you (or someone) mind making a step-by-step tutorial on how to format and partition an external drive to put linux on it?  That would help me out a TON.

---

### Post by pxwpxw on 2007-09-29
> **cheezle said:**
> Ooh, thanks!  I've been considering getting an external hard drive to mess around with linux on rather than partition my internal drive.

Would you (or someone) mind making a step-by-step tutorial on how to format and partition an external drive to put linux on it?  That would help me out a TON.



 Depends on how big the drive is and what you want to put on it and whether your mac supports external firewire  MacosX booting. 

 But the short answer is assuming its around 200 GB, just use the Macosx partitioner to make 4 equal Apple macos extended partions, not journalled. 
 Then use the ubuntu installer to delete one (50 GB) and then let it automatically install in the free space. 
 You can install MacosX in the first one to see if it boots from the external if you like.

Some external **firewire** drives can be installed successfully just using the standard ubuntu installer.
 
 My WD MiBook 300GB with Ubuntu 704 using  firewire, installs with a bootstrap partition on either the internal or the external drive and standard boot installer.
 
Some other firewire externals need post-install fixups or a patch to the  "ofpath" installer script to recognise their type.  
[COLOR="Red"]
Patch at launchpad bug report here:, support the bug report if you want ubuntu to do anything about it.
 
ofpath patch for yaboot installer.
[https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607)[/COLOR]

---

### Post by cheezle on 2007-09-29
It's ok, I think I've decided on just re-sizing my osx partition, and using the free space for linux.  However I'm not *quite* sure how to go about this, and I posted my question in the "Powerbook G4 12", Feisty... What am I doing wrong?" thread.

---

### Post by pxwpxw on 2007-09-29
> **prestosd said:**
> Hey, just found out that if you switch the line to ```
default=macosx
``` it should boot Mac OS X! :)

Yes, but that only works on the first stage of the boot (ofboot.b). So you only get it when the full yaboot install is done.:(

---

### Post by idkwot on 2007-10-01
> **pxwpxw said:**
> Yes, but that only works on the first stage of the boot (ofboot.b). So you only get it when the full yaboot install is done.:(

true story

---

### Post by pxwpxw on 2007-10-05
A successful installation on external usb HDD, with boot partion and kernel on the internal HDD.  And the exterrnal partition system was DOS MBR.

**Lo'oris **
Installing on an external usb drive... on a mac!
[http://ubuntuforums.org/showthread.php?t=561167](http://ubuntuforums.org/showthread.php?t=561167)

---

### Post by Lo'oris on 2007-10-07
I'll now try to remember the main steps I did.

· full backup
· use ubuntu **alternate** cd to install it in the free space of the usb drive. I told him "use as you wish available space"
bug: it created a partition to be used as /boot, but it left it empty and unformatted. It doesn't matter much.
· boot ubuntu **normal** livecd. There should be 100MB free near the start of hda (the internal hd). Use fdisk's command "b" to create an apple_bootstrap partition at the start of that free space
· use gparted to create an hfs (non-plus) partition after that (it will become /boot)
· run yabootconfig that will write data to the apple_bootstrap partition
· put the kernel in the new /boot
· modify /etc/fstab accordingly
· run ybin -v
· modify /etc/yaboot.conf and run it again

PLEASE notice I probably forgot something, or switched the order of some steps, or whatever. Don't take these guidelines as a goldmine, use them only if you're a diehard hacker and you think you can handle situations that I didn't consider. I take no responsabilities : )

---

### Post by MichaelBarkowski on 2008-05-03
How do I copy the yaboot files?  Mac OS X cannot read the ext2 formatted firewire disk.  Can I get them off the ISO?  Or is there some ext2 driver for Mac OS X?

---

