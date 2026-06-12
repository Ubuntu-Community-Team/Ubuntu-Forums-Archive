---
title: "Ubuntu installed on separate HD, Vista not showing up"
date: 2009-05-21
forum: Apple Hardware Users
---

### Post by PPCtoFREE on 2009-05-21
Ok, now that I look at the forums it looks like I should have done this in a different way and I cannot find any particular threads explaining how to fix my particular issue yet. I apologize if this has already been answered but I haven't been able to find it.

So here is the issue. I have a Mac Pro 2006 I have Leopard installed on my Bay 4 drive (sdd2) and it is partitioned with Vista installed on it as well (sdd3) but not through Boot Camp. I decided I liked Ubuntu so much that I wanted to install it on a separate drive instead of playing with it on my netbook. So I converted the drive in Bay 1 over to Ubuntu which it is on (sda3). Well, now I can no longer see Vista.

I tried booting up with the Vista CD to repair the disk, and make it be recognized as a startup disk again, but that didn't work. It doesn't recognize it as being a startup disk, though I can see all of my files from Vista, nothing got deleted or written over. I do not see it in grub 2 when my computer boots into Linux. I tried editing grub as this worked with my netbook when I couldn't see XP after installing Ubuntu on it.

This is what I have listed in Grub:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		24b52927-0cf5-470b-95ae-da7425ddd45b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=24b52927-0cf5-470b-95ae-da7425ddd45b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		24b52927-0cf5-470b-95ae-da7425ddd45b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=24b52927-0cf5-470b-95ae-da7425ddd45b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		24b52927-0cf5-470b-95ae-da7425ddd45b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd3
title Windows Vista Ultimate
root (hd3,1) - *[COLOR="Red"]I have tried changing this to hd3,0 hd3,2 hd,3 None of them seem to work[/COLOR]*
savedefault
makeactive
chainloader +1

I really don't know what else to do. Does anyone know how to make this work without me re-installing any OSs? Thank you in advance!

---

### Post by pxwpxw on 2009-05-22
From the grub  menu, C will get a grub> command line, and it can find Ubuntu and Vista, as seen by grub.

```

grub> root (hd0)
grub> find /vmlinuz
grub> root (hd3,2)
grub> find /              then press <TAB> not return

```

The  find /vmlinuz should find ubuntu, or try (hd1) and other drives; 

And after find / <TAB> with no 'return', it should list files it can see in the root of (hd3,2), or you can try other drives,partitions and to find Vista.

Pleas also post from ubuntu
```

$ ls /boot/grub/

```
To check what grub files are installed.

---

### Post by PPCtoFREE on 2009-05-24
Well, I finally had a chance to look back into this.

I tried the find / <TAB>

on all of the partitions but got either errors or it told me something about there being nothing to mount.

Below you can see where Vista is from a snapshot of GParted.

[ATTACH]115023[/ATTACH]

---

### Post by PPCtoFREE on 2009-05-24
Well, I finally have it figured out. 

After more searches for other options, I came across the rEFIt bootloader.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

I made a bootable rEFIt CD just to check it out before installing. Upon booting with the CD I was at least now greeted with the Vista hard drive as an option for booting again. It still did not boot from it **but** I was now given a new error code: "BOOTMGR is Missing". So I searched for that on Google and found that I need to run the repair function from the Vista disk. So, for some reason, the Vista DVD didn't notice the Vista startup, as a valid startup disk that needed repair till after running rEFIt. Not sure what the reason is, but I am just happy I didn't have to go through the process of reinstalling Vista.

Now I am the happy owner of a tri-boot Leopard, Ubuntu, and Vista Mac Pro.

Thanks for the help and I hope this helps anyone else that comes across this same issue. :D

---

