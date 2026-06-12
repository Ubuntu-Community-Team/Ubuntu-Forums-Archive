---
title: "Error 17: Cannot Mount Partition on boot"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by ajmedfor on 2007-08-30
I am working on my brother's computer, which already has Windows. I used the live cd, chose install, and resized the windows partiton (sda1) to 50 gb (of 250). I then created a FAT32 partition in sda2 which was 180 GB and mounted to /files.  Next, I made a 2GB swap partition in sda3, and finally an 8GB ext3 partition in sda4 which mounted to /. The install continually gave me an error about not being able to mount the /files partition, so I tried leaving the mount point blank. This allowed the install, but on boot gave me an "error 17, cannot mount partition." I then tried to use the partition manager on the windows setup disk to delete all partitions, and then used the program cute partition manager to create the 180GB partition. I tried the install again, and this time it allowed me to install with /files listed as a mount point, but still gave the "error 17" message on boot. I again booted from the live cd, and was able to mount the root partition in the live session, but not able to mount the 180GB partition, so I edited the fstab in the root partition to not auto-mount the 180GB partition, but I am still getting the "error 17" message. Can someone please help??

---

### Post by logos34 on 2007-08-30
error 17:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

You might consider mounting sda2 at '/home'.  (More on [separate home partition here]("http://users.bigpond.net.au/hermanzone/p14.htm")).

---

### Post by ajmedfor on 2007-08-31
ok... I found the mistake in menu.lst, grub was trying to boot hda(0,0) instead of hda(0,3). I made  the change, and now ubuntu starts to boot but hangs up for about 5 minutes and gives the error 

Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modues ls /dev
ALERT! /dev/hda1 does not exist. Dropping to a shell
BusyBox v1.1.3 etc
/bin/sh: cant access tty: job control turned off
(initramfs)_

and I can access all the files on root through the command line. I only have one hard drive, and am assuming this is a problem somewhere in fstab? can anyone help?

---

### Post by bodhi.zazen on 2007-08-31
Can you post the relevant stanzas from /boot/grub/menu.lst and identify your root partition ie /dev/xxx ?

---

### Post by logos34 on 2007-08-31
> **ajmedfor said:**
> 
ALERT! /dev/**[COLOR="Red"]h[/COLOR]**da1 does not exist. Dropping to a shell

...and I can access all the files on root through the command line. I only have one hard drive, and am assuming this is a problem somewhere in fstab?

sound like it.  maybe it's just as simple as correcting a typo--'sda1' instead of 'hda1'...might want to post fstab file too.

---

