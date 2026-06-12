---
title: "Please insert cd and hit enter...?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Scarlett on 2007-01-31
I've been putting off resizing my HD for a while because I was afraid I'd mess it up.  It finally got to a point where I had to do it and sure enough... I borked it.  I messed up Grub somehow and kept getting an error 17.  So I reinstalled from the Edgy CD and things were going relatively well until some of the things I want to install  will get about 62% done and then I'm prompted to put the CD in the drive to continue.

I was able to install Gparted and it looks like I've somehow mounted hdb1 in "/, dev/.static/dev".  I don't know if that's actually the problem but I don't remember it being there before.  Anyway, how do I make it not ask for a disk when I'm trying to install stuff?

---

### Post by Scarlett on 2007-01-31
Well, booting from a live Gparted CD didn't work but I did figure out how amazingly easy this would have been if I'd done it that way to begin with.  (Ha, joke's on me.)

I checked out a grub tutorial:  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
and about halfway down the page there's a an example of what a grub menu should look like.  I noticed that on theirs root is listed as (hd0,1) and mine isn't.  Can I just edit that or will that really screw things up?

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

When I did sudo gedit to pull up the menu I also got this warning:

(gedit:5623): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Should I just reinstall and if I do, how I make sure everything gets to where it's supposed to be?  There used to be screen shots of the install process but I couldn't find it.  Does anyone have a link to that?

---

