---
title: "kernel panic!"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by bananacolasnack on 2005-05-15
I want to install ubuntu on my external USB hard drive so that I can choose to boot with either operating systems. First I tried to install it to the free space on my external hard drive, then I tried clearing it. I got the same error both times, this is what the screen looked like after grub:

uncompressing Linux...0k, booting the kernel
audit(111615804.454:0) initialized
Starting Ubuntu...
pivot_root:No such file or directory
/sbin/init:428:cannot open dev/console: No such file
kernel panic - not syncing: Attempted to kill init!

Please get back to me when you can about this problem. Thanks

---

### Post by Kimm on 2005-05-15
you seem to have a file missing...

---

### Post by monchichi on 2005-05-15
It's seems that the kernel isn't loading a crucial module or two that are necessary to boot from such a drive. You will need to build a new initrd.img to have the kernel automagically load those modules.

Try the following:
```
sudo gedit /etc/mkinitrd/modules
``` and add the following modules to the file: 

sd_mod
ehci-hcd
uhci-hcd
ohci-hcd
usb-storage

Then run:```
mkinitrd -o /boot/initrd.img
```Check the bottom of the file "/boot/grub/menu.lst" and make sure there is a line in between "kernel" and "savedefault" that reads: "initrd     /boot/initrd.img"

Hope this helps!

EDIT: I just realized that you probably can't boot into Ubuntu at all, in which case you could probably do all of this using a live-cd.

---

### Post by fanoodlehey on 2005-05-26
I've been having this same problem and it looks like I need to rebuild my initrd with these modules. I am using a Live CD (Beatrix) to try to edit files on my usb drive and run mkinitrd but I think that mkinitrd is trying to run at a live cd level and not change my initrd.img on the usb hard drive (sda1).

Then I tried to unzip the initrd.img which I renamed to initrd.gz and it is not a valid gzip file. So I can't edit the initrd manually.

Any ideas?

---

### Post by fanoodlehey on 2005-05-30
Never mind.

Got it working using [http://ubuntuforums.org/showpost.php?p=42546&postcount=14](http://ubuntuforums.org/showpost.php?p=42546&postcount=14) .

The nano /target/boot/grub/menu.lst step did not work for me so I just went ahead with the reboot and when grub failed I edited the steps manually. Then I finished installation and edited menu.lst with gedit in ubuntu.

---

