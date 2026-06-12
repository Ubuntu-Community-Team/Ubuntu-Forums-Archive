---
title: "Won't boot grub"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by iamzachyouarenot on 2007-03-08
First off, 
    I'm new to the forums. I upgraded to Ubuntu from windows late last week, wiping the drive and devoting the whole machine to Ubuntu.
    I had some problems loading it. I got the live cd to work fine, installing from there. Whenever the computer would start to load it would go right to a screen that says "GRUB" and has a blinking cursor. No error codes, no more loading..just grub and blinking cursor.
    After looking through here and talking to some friends who already had it installed, I got it to boot from the cd, then it runs fine..i can take it out and do anything else untill i need to start up again, then I have to put the cd back in.
     I activated the swap partation in hopes that maybe some boot files had been put in the wrong place, but no luck.
    I can't see any problem in grub and besides this everything works fine.

Any Ideas?

---

### Post by mahy on 2007-03-08
you can search the Web for menu.lst file adjust it a little bit and place it to /boot/grub directory.

---

### Post by dstew on 2007-03-08
Here is what is happening. When you start your system, the grub boot loader is starting, but it cannot find its configuration file (its "menu"). When it cannot find this file, it drops to a command line.

You can do many things from the command line, one of which is look for grub's configuration file using the "find" command.

grub> find /boot/grub/menu.lst

If it cannot find this file, you may need to re-install grub, which you can do from the grub command line also.

---

### Post by iamzachyouarenot on 2007-03-08
Here's what the menu.lst looks like now (without all of the #'s). I found a bunch of things and can't figure out what to change

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot


and it found it fine on (h0,0)

---

### Post by iamzachyouarenot on 2007-03-08
Thanks for the quick responses, by the way.

---

### Post by dstew on 2007-03-08
For some reason grub is looking in  the wrong place for its menu. You can easily re-setup grub from the grub prompt. First make sure that stage1 is present on the hd0,0 partition.

```
grub> find /boot/grub/stage1
```

It should return (hd0,0), like it did for menu.lst. Then, re-setup grub:

```
grub> root (hd0,0)
grub> setup (hd0)
```

This will put the grub stage1 booter into the master boot record of the first disk, and cause grub to go to the hd0,0 partition to find its stage2 and the menu. Reboot and you should get the menu. The menu items look fine to me.

---

### Post by iamzachyouarenot on 2007-03-08
it's giving me an error

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup(hd0)

Error 27: Unrecognized command

---

### Post by dstew on 2007-03-08
Make sure there is a space between setup and (hd0).

---

### Post by iamzachyouarenot on 2007-03-09
tired it

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


rebooted...same problem. GRUB screen with flashing cursor

---

### Post by dstew on 2007-03-09
Wow. No errors, and no dice either. What happens if at the grub prompt you enter the boot sequence? That is, type the commands that are in your first menu item. Make sure that your kernel is in hd0,0 using

grub> find /boot/vmlinuz-2.6.17-11-generic

If it is, then enter the following:

grub> root (hd0,0)
grub> kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
grub> initrd /boot/initrd.img-2.6.17-11-generic
grub> boot

My guess is that your kernel may not be in the hd0,0 partition, and since the menu tells grub to be quiet, it doesn't find it, and doesn't tell you anything.

---

### Post by iamzachyouarenot on 2007-03-11
grub> find /boot/vmlinuz-2.6.17-11-generic
  (hd0,0)

grub> root (hd0,0)

grub> kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash

grub> initrd /boot/initrd.img-2.6.17-11-generic

Error 16: Inconsistent filesystem structure

---

### Post by dstew on 2007-03-11
Not good. That error indicates a possibly corrupt file system. See grub errors in

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

You might need to reformat.

---

