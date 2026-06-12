---
title: "installing drivers"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by joelclyne on 2005-06-23
Hi, Im having a bit oftrouble installing a driver. Im very new to linux  but have tried folling all instructions found to no avail.

Its for an iomega buz video capture card

Ive logged onto the root terminal
updated an essential package by typing 
sudo apt-get install build-essential

there is already a makefilein my uncompressed folder but when I type ./configure I get this message
sh: ./configure: No such file or directory

there isnt a file called configure in my uncompressed folder

if I type make (as Im sure I read that configure makes a makefile file which is included) I get the message 

Making Unified Zoran (zr360x7) driver for 2.6.10-5-386 kernel...
/bin/sh: line 0: cd: /lib/modules/2.6.10-5-386/build: No such file or directory
make: *** [here] Error 1

can anyone please help. Im happy using comand prompts but id I should use the synaptiv package manager to do this Im happy to (if you tell me how to) . 
I dont understand whatit doesorhow it works yet

cheers
joel

---

### Post by joelclyne on 2005-06-23
Sorry to bump my own thread but Im really stuck, can anyone help or point me in the right direction.
the instructions I got for the tar file  is from [http://mjpeg.sourceforge.net/driver-zoran/downloads.php](http://mjpeg.sourceforge.net/driver-zoran/downloads.php)

and the drivers  files are linked to at the top of that page.

Any help would be greatly appreciated
cheers
joel

---

### Post by N'Jal on 2005-06-23
It says quite largly NOT to use this driver file if you use a 2.6 kernel and ubuntu uses's the 2.6 kernel's and unless you have rolled your own previous kernel... but i really don't see why you would do this.

> The driver is included in your 2.6.x kernel. Therefore, if you're running a 2.6.x kernel, do not download this driver

It's instruction's say

```

$/sbin/modprobe zr36067

```

That should be it, i presume, i don't know since i don't have this card. Hope it helps

---

### Post by Ashims on 2005-07-09
Aparently the zoran module isn't included by default in ubuntu's kernel package... I dunno... I'm gonna figure out the specifics of this now... I'll post what I find (maybe in a new thread-- but I'll link it).

Cheers.
Ash.

---

### Post by DamienMcKenna on 2005-09-26
Any luck with this?  I installed Ubuntu for the sole purpose of video grabbing with my Buz drive.

---

