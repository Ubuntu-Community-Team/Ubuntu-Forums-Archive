---
title: "A question.."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Jamson on 2006-09-28
Hi,

I really like Ubuntu, but before i install it i have a question i would like answering before i install it onto my hard drive. I had a play around with it on the Live CD and really liked it!

1. I want to install it on my hard drive, but i want to keep my current boot loader (The standard Windows XP one) and would like to boot Ubuntu through a floppy disk. Is that possible.

Thanks! :)

---

### Post by ian.l on 2006-09-28
I'm pretty sure this is possible, using the grub-install command and a properly configured grub.conf. But I haven't done it before, so I'll have to leave the step-by-step to someone else. Anybody?

---

### Post by meborc on 2006-09-28
why don't you just make the default boot option windows and think time 2 seconds... then when bootup it will boot to windows with practically no delay... and when you want to play around with a bit better software, you just need to hit the "up" key a few times when the list of boot options is presented... or do you need to conseal the existance of ubuntu? :mrgreen:

---

### Post by confused57 on 2006-09-28
> **Jamson said:**
> Hi,

I really like Ubuntu, but before i install it i have a question i would like answering before i install it onto my hard drive. I had a play around with it on the Live CD and really liked it!

1. I want to install it on my hard drive, but i want to keep my current boot loader (The standard Windows XP one) and would like to boot Ubuntu through a floppy disk. Is that possible.

Thanks! :)

You could use the alternate cd and install grub to floppy:
[http://www.ubuntuforums.org/showthread.php?t=188819&highlight=grub+floppy](http://www.ubuntuforums.org/showthread.php?t=188819&highlight=grub+floppy)

The desktop live cd doesn't give you the option of where to install grub, it automatically installs grub to your mbr.

---

### Post by Jamson on 2006-09-28
Oh ok..

Is there another way to do it without downloading the alternative cd? (I have dialup, and the friend that gave it to me doesn't want to re-download another copy :()

Can i install Ubuntu, then within Ubuntu install a grub boot loader onto the floppy disk?

---

### Post by bodhi.zazen on 2006-09-28
Yes it should be easy.

Install Ubuntu.

When it asks where to install GRUB, install into the Ubuntu root partition
[color=red]NOT the MBR[/color]

Now boot to the live CD.

Make a grub floppy:
First insert a floppy, then
```
mke2fs /dev/fd0
sudo mount /dev/fd0 /mnt/floppy
sudo mkdir /mnt/floppy/boot/grub
```

Now copy the files stage1, stage2, and menu.lst from /boot/grub to
/mnt/floppy/boot/grub.

Now:```
sudo grub
```

At the grub prompt:
```
root (hd0,1) (susbtitute your buuntu partition in Grub speak partition).
setup (fd0)
quit
```

---

