---
title: "installing hardy on ppc xserve (no ide-core?)"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by d^2 on 2008-06-22
hello,

i've been struggling mightily to get ppc ubuntu 8.04 up and running on a g4 1.33ghz xserve.

at this point, i'm stuck in busybox.  i try to "modprobe ide-core" and i get a fatal error about there being no such module.

where should this module be located?  maybe it literally isn't on my livecd (and thus not on my installation)?

other info:
the live cd works without a hitch.  i am able to log in that way and edit the files in my installation.

installation appeared to go without a hitch.

from livecd, i tried to add "ide-core" to my etc/initramfs-tools/modules and to my usr/share/initramfs-tools/modules.  then i chrooted to my installation and ran the "sudo update-initramfs -u" command.  still nothing.

the options passed to yaboot are "quiet splash".  i do see the splash screen with the little bar moving back and forth for a while, and then busybox.  can i do "nosplash" and see all the text get dumped out?  maybe there is an error message in there somewhere?

the harddrive is at /dev/hde, with hde2 for yaboot, hde3 for root and hde4 for swap.

this is tough without any log files!

any suggestions?

---

### Post by d^2 on 2008-06-22
a little more info:
in busy box, i tried this:

(initramfs) modprobe -l | grep ide-

and this showed me these modules:
ide-disk
ide-generic
ide-cd
ide-floppy
ide-tape
ide-scsi

so i tried "(initramfs) modprobe ide-disk" instead of "ide-core", and i didn't get any errors, but when i try to exit busybox, i still get this error on virtual terminal 1:

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hde3 does not exist.  Dropping to shell!

indeed, when i tried this:
(initramfs) ls /dev | grep hd

i get only "hda".  how to get it to recognize hde?

---

### Post by stream303 on 2008-06-22
If you could post your yaboot.conf that would be very helpful.  Also what slot is this drive installed to?  How many drives are in that box?

I have a feeling that for some xserves, relying on open-firmware aliases, instead of specifying device id's , may help ease installation.  Check this thread out for some powermacs that may be having the same issues:

[http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)

In other words, you may want to use OF aliases like

[b]device=hd:
ofboot=sd3:3[/b]

etc.

---

### Post by d^2 on 2008-06-22
i think i was heading beginning to suspect this already:

i have a suspicion that when i reboot, my harddrive is getting mapped to /sda instead of /hde.  i didn't realize this could happen.

i am actually booting off a usb stick that i created from the live cd, since my cd drive doesn't work, and it is mapped to sda when i am in the live environment (which is why i think that once it is out of the way, the harddrive takes over sda)

my xserve has 4 hot swappable slots, and i only have one drive in the first slot (i imagine it's number 0).

here is my yaboot.conf:
```
boot=/dev/hde2
device=/pci@f2000000/AppleKiwi@15/@0/disk@0:
partition=3
root=/dev/hde3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="quiet splash"
```

i think the device is not right here.  in open firmware, i see a device alias that looks like this:
/pci@f2000000/AppleKiwi@15/ata-6@0/disk@0

how do i use the device alias instead of using /dev/hde?  i tried to just switch it to sda, but i got an error.  maybe if i change it to sda and change the device?

thanks for the help so far, it's got me thinking in a different direction.

---

### Post by pxwpxw on 2008-06-23
d^2

I think none of the above. I don't understand how you got /dev/hde for the hard drive if it is the only one, should be hda and the usb stick will be sda, thats normal on a G4 iBook here, also there is no ide-core module here (cant see why Xerver would differ).

The fact you got as far as
```
 
  (initramfs) ALERT! /dev/hde3 does not exist. Dropping to shell!

```

indicates that the problem is probably just an incorrect root=/dev/hde3. You have only 1 drive, should be /dev/hda.

The ide-core module is not used on  some g4 (mine).

yaboot can find the kernel and initrd without a device= statement if they are on the boot drive. 

Need to confirm where and what the partitions are. 

Can you do the following and post results to clarify.

Boot the USB stick, and run
```

$ sudo mac-fdisk -l

```

Then with the usb stick still plugged in, boot from the xserver hard drive to busy box and run and note
```

(initramfs) cat /proc/partitions

```

---

### Post by d^2 on 2008-06-23
i agree, it's very confusing that i have my drive mounted as hde.  i am guessing it is because the harddrive should have been mounted as /dev/sda, but this was already taken by the boot device.  (there is an ata controller in there (pdc2027x), and i am guessing that would cause it to be sda instead of hda)

here is the output of mac-fdisk (when i'm booted off the USB):
```
/dev/sda
system
/dev/sda1 Apple_partition_map Apple     63      @ 1    (31.5k)
Partition map
/dev/sda2 Apple_Bootstrap     bootstrap 1600    @ 64   (800.0k)
NewWorld bootblock
/dev/sda3 Apple_Free          Extra     3905919 @ 1664 (1.9G)

Block size=512, Number of Blocks=3907583
DeviceType=0x0, DeviceId=0x0

```

here is the output from cat /proc/partitions in busybox (very cool, i wasn't aware of this):
```
8  0 58615704 sda
8  1 31       sda1
8  2 977      sda2
8  3 57108398 sda3
8  4 1506296  sda4
8 16 1953791  sdb
8 17 31       sdb1
8 18 800      sdb2
8 19 1952959  sdb3
```

this was what i guessed was happening... the sda listed here is my hard drive and sdb is now the usb.

i'm confused about how to resolve this in yaboot.conf. when i am booted off the usb stick, i set boot=/dev/sda2 and it writes back to the usb stick (oops -- need to fix the usb stick now!).  so i have to set boot=/dev/hde2 which is where the device is when i'm booted off the usb stick.  catch-22?!

thanks!

---

### Post by d^2 on 2008-06-23
SUCCESS!

here is what i had to do to make yaboot boot the sda drive.
1 - mounted /dev/hde3 at /mnt
2 - editing the yaboot.conf on /mnt/etc/yaboot.conf:
```

# this stays as hde2 so that we write the yaboot info to the correct drive
boot=/dev/hde2
device=hd:
ofboot=hd:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
```

note that i checked that hd was pointing at the correct drive before i tried this (hd is the first detected hard drive):
```
> cat /proc/device-tree/aliases/hd ; echo
```

which, in this case, gave me this:
```
/pci@f2000000/AppleKiwi@15/ata-6@0/disk@0
```

after all these changes, i ran "sudo ybin -v -C /mnt/etc/yaboot.conf" and crossed my fingers.  no errors, so i rebooted!

note that the yaboot info is written to the drive at "boot=", so i had to leave that as hde2 while i was booted off the USB and the harddrive was mounted as hde.

i knew that the drive was going to be mounted at sda3 when it rebooted, so i set root to point at that.  (is there a way to do this without "hardcoding" the sda3?)

the only thing i have to do now is to change that boot=hde2 to boot=sda2 now that i am in the hard drive OS and not the USB OS.  (for future edits of yaboot, like kernel updates)

thanks for all the ideas!

---

### Post by pxwpxw on 2008-06-24
:)

Nicely done, hope it all works now, and right about fixups for subsequent re runs of ybin. 

In yaboot.conf, is  ofboot=hd: a typo?
should be ofboot=hd:2 ,the bootstrap partition?

Don't know any other way to specify the linux root partition except in yaboot.conf, or it can be done from an open firmware prompt, see man yaboot.

That "hde" is a mystery, here are some suggestions after fiddling with G5 powermac and G4 iBook-

Apparently "hde" is the way the installer names the ata drive when it finally installs yaboot, after the hd root partition is built in /target, thats when it writes yaboot.conf and the bootstrap files, but it is "sda" in the end as seen by the installed and booted hardy 804 system. 
 
When booted from the usb installer, if you run mac-fdisk -l as root, you should have seen both drives listed, as in /proc/partitions, it has a permissions problem otherwise, and "hda" is the cdrom drive on this g5 box.

But the installer can also name drives differently before and after it has built the /terget/ root system, so I assume you did not get "hde" in earlier partitioniong for the install.

I recently installed hardy to an external firewire drive on G5 ppc, and the target drive was initially /dev/sda  and finally sdc ( 2 internals sda sdb, external sdc), but that was finally correct without intervention. 

There was also a point in the recent ubuntu i386 versions (and deban i think) where ide drive names changed from hd* to sd*  and then there were changes from ata to sata.

Plus you suggest there seems to be some special treatment by the installer for the xserve controller? AppleKiwi@15 ?

BTW was there any special trick in gettting the desktop installer CD onto a usb stick?

EDITED:
and "hda" is the cdrom drive on this g5 box.

---

### Post by d^2 on 2008-06-24
no, the "ofboot=hd:" is not a typo.  i sort of guessed on this one.  maybe it is redundant?  maybe "device=hd:" is enough for yaboot to guess where everything is?

for making a bootable USB stick (drive?) i followed these instructions:
[http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320)

this actually worked exactly for me (there are a couple typos, but they are very minor).  i was really lucky that my girlfriend has a ppc laptop that was able to boot the live CD so i could build the USB.  my Xserve cd drive is broken, and the mac osx that was on it was corrupt (talk about expensive brick)!

---

### Post by pxwpxw on 2008-06-24
> **d^2 said:**
> no, the "ofboot=hd:" is not a typo.  i sort of guessed on this one.  maybe it is redundant?  maybe "device=hd:" is enough for yaboot to guess where everything is?

for making a bootable USB stick (drive?) i followed these instructions:
[http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320)

this actually worked exactly for me (there are a couple typos, but they are very minor).  i was really lucky that my girlfriend has a ppc laptop that was able to boot the live CD so i could build the USB.  my Xserve cd drive is broken, and the mac osx that was on it was corrupt (talk about expensive brick)!


Thanks thats a good howto, will try it.

The ofboot= is not needed if you are booting yaboot directly from openfirmware as with your usb stick installer, but it is normally needed if you are booting automatically via the first stage ( ofboot ) from a standard yaboot install, which makes ofboot the type tbxi file (as done by mkofboot or ybin). But maybe you have a special case there.

edit:

From the hard drive installation, **yabootconfig** will do it all for you by writing a minimal 
 /etc/yaboot.conf,  (saves /etc/yaboot.conf.old) and the bootstrap files. It uses 
 /usr/sbin/ofpath to find any open firmware paths.
 
```

 sudo yabootconfig --debug

```

---

### Post by toddobryan on 2008-08-02
The hde problem isn't related to the USB taking sda--I get the same thing booting from CD.

Remember that the XServes use SATA drives in SCSI adapters or somesuch weird setup. I wish I had been able to find this while I was at school playing with the XServe, because I was having exactly the same trouble.

I'll let you no if I have any success on Monday.

---

