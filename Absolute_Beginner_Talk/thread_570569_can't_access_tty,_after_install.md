---
title: "can't access tty, after install"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Lee_Lee87 on 2007-10-08
I've already read all the other threads on this topic, but they all seem to happen during install.
I've already have it installed and it was working fine for the first few boots. Originally I tried
modifying the /initramfs-tools/modules by adding piix and updating it, didn't seem to work.
That is, if I modified it correctly. 

# examples:
#
# ???????? (don't rem. what this said)
# ???????? (same here)
# piix (This is the line I added)

or should it just have been?
piix

I've also read about issues with grub and uuid. I'm starting to lean towards grub, since all of my drives are sata. I'm not really sure how to check or how to modify the grub files.
My System Specs
feisty 7.04 (x86)
e6850
2x1GB ram
8600gts
Sata WD Raptor 150GB
Sata DVD-Drive

Any help would be greatly appreciated.

---

### Post by Dr Small on 2007-10-08
Pound symbols (#) mean comments, as you can see the other lines are commented out by the pound symbol also. You would have to remove the pound symbol to have it actually read that in the configuration instead as a comment.

Dr Small

---

### Post by Lee_Lee87 on 2007-10-08
I'm longer able to boot into ubuntu though, so how would I go about modifying the file?

---

### Post by Dr Small on 2007-10-08
Can you access GRUB and boot in recovery ?

---

### Post by Lee_Lee87 on 2007-10-08
Nope, eventually shoots out the same tty error

---

### Post by Lee_Lee87 on 2007-10-08
Well, for some strange reason I was able to boot up and get in, I remodified the initramfs 
(removing the #) updated it. Restarted, and am still facing the same error. So can anyone let me know 
how to modify GRUB to mount sda instead of hda. this seems to be the problem in other threads.

---

### Post by Lee_Lee87 on 2007-10-08
Well, I'm getting closer, I've found a way to get it boot into ubuntu a little more frequently. Simply 
enter the grub menu at boot select the first kernal then edit the kernal line and add 
ramdisk=8192 to the beginning of the line, then boot it up. Now only question is how do 
I modify grub to boot properly, This is what fstab shows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=973a11da-97f7-4073-8760-0d162eb2a8ee /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7939c0da-75b4-4b4b-9fbf-75a001e9b011 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and this is what grub shows

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=973a11da-97f7-4073-8760-0d162eb2a8ee ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=973a11da-97f7-4073-8760-0d162eb2a8ee ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=973a11da-97f7-4073-8760-0d162eb2a8ee ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=973a11da-97f7-4073-8760-0d162eb2a8ee ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

so my question is what do I change so that it will boot properly?

---

