---
title: "Reinstalling Grub"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Zilphanael on 2007-10-12
So I just installed TinyXP Beast onto my laptop, but this means that Windows overwrote Grub.  I'm trying to reinstall Grub from my Ubuntu Live CD, but "find /boot/grub/stage1" doesn't work from Grub OR from Terminal.  My Ubuntu partition is /dev/sda4 (I believe) and my TinyXP partition is /dev/sda7 (I believe).  I've also been advised to manually mount my Ubuntu partition, but I don't know what I should put in for "fstype" in my mount command.

Please help as much as possible.

Thank you for your time!

---

### Post by Duck2006 on 2007-10-12
From the terminal on the live cd type

sudo grub

find /boot/grub/stage1      "it will come back with some thing like (hd0,0)

root (hdx,y)                      "what find came back with is in place of x,x"

setup (hd0)

quit

then reboot and grub sould be there for you.

---

### Post by Zilphanael on 2007-10-12
As I believe I already stated, "find /boot/grub/stage1" returns Error 15: File Not Found.  Thanks, though.

---

### Post by Duck2006 on 2007-10-12
From the terminal in the live cd type

sudo fdisk -l

and post the output

---

### Post by nick_h on 2007-10-12
Re-install grub first by typing:
```
sudo apt-get remove grub
sudo apt-get install grub
```
and then follow Duck2006's instructions.

---

### Post by Zilphanael on 2007-10-13
Managed to solve on my own, thanks though guys.  The trick was finding where the actual file was (not where it was supposed to be).

---

### Post by ronmarley1 on 2007-10-13
Another option would be to use the Super GRUB Disk at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Boot the CD and it'll find GRUB for you and restore it.  Worked for me many times.

---

### Post by nick_h on 2007-10-13
> The trick was finding where the actual file was (not where it was supposed to be).

Where was the file?

---

