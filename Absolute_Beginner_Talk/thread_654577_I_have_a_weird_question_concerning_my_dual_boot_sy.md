---
title: "I have a weird question concerning my dual boot system, Grub, and Windows Vista"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Jeff Kowalski on 2007-12-31
I'm running Windows Vista on my laptop, and in the mess of trying to install the distro of my choice from the hard-drive, I installed Wingrub and essentially made my Vista partition unbootable. I'm working right now from a Linux Mint distro because I had the LiveCD lying about. I know this isn't an Ubuntu question, but I had no idea where else to go for help. Does anyone know how to fix the bootfiles on both OSes so I can boot back to Vista?

---

### Post by fiddledd on 2007-12-31
There's probably other ways, but Super Grub Disk will restore Grub etc.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by anthonie on 2007-12-31
As you're already in Mint Live (I suppose) this is as easy as it gets.

a. Open a terminal window
b. Type "sudo grub" your prompt should change to grub, if so
c. Type "find /boot/grub/stage1
d. Type "root (hdx,x)" fill in your previously obtained hdd and boot mountpoint 
e. Type "setup (hdx)" without the second digit!
f.  Quit grub, type "quit".
g. Reboot.

---

### Post by Jeff Kowalski on 2007-12-31
I'm actually working from a Mint partition.

Here's what GParted tells me: hda1 is Vista, formatted in ntfs & hda2 is Mint, formatted as ext3.
Grub can't mount the Vista partition for some reason.

Would my best bet be to just get rid of this Mint partition, resize the Vista one to use the whole hard disk, and try setup in grub again?

---

### Post by anthonie on 2007-12-31
Have you taken into account that Grub counts from zero? So, if your fdisk -l output tells you you have hd1 as Vista, it has to be hd0 in Grub and so on.

---

### Post by Jeff Kowalski on 2007-12-31
Okay, now I'm on Live Mint, and my Vista partition now takes up the entire hard disk. I enter grub in the terminal, enter "find /boot/grub/stage1" and get "Error 15: File Not Found", even though when I check through the file browser, it's totally there.

---

### Post by anthonie on 2007-12-31
You probably did not start grub being root. Try sudo grub.

---

### Post by Jeff Kowalski on 2007-12-31
I got the same error.

I looked around through some other threads, and one of them suggested downloading ms-sys through the repositories and using that to restore the MBR, so I did, but now the bios doesn't find the the OS at all.

I'll keep looking around, but any help you guys provide is greatly appreciated. I'm already learning a lot about grub and OS loading as a direct result of my own screwup. :-p

---

### Post by anthonie on 2007-12-31
If that's the problem, my best experiences are with a little program that is also included in the Gparted LiveCD, it's called testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can find it at the adress above.

---

