---
title: "X.org crash after upgrade to radeon 9800"
date: 2007-07-24
forum: Apple PPC Users
---

### Post by onefriedrice on 2007-07-24
I recently upgraded my video card from GeForce2 MX to a Radeon 9800 Pro.  It works much better in Mac OS X, but it causes a X.org server crash in feisty.  I read a few other (related) bug reports and posts, but I still haven't figured it out, so sorry if this is a duplicate.

The (WW) is this: Invalid IO Allocation b:0xf0000400 e:0xf00004ff correcting^G
and the (EE) is: end of block range 0xefffffff < begin 0xf0000000

Sorry no logs to post, but it seems from the backtrace that the int10 module is trying to read the BIOS.

Installed is xserver-xorg-video-ati (6.6.2-0ubuntu6) - the latest, I assume.

I'll post more info later if this isn't enough because I have to be somewhere else now, but maybe someone can point me in the right direction just from this info.

Thanks!

---

### Post by bigfox on 2007-07-24
Try typing this at a command prompt

sudo dpkg-reconfigure -phigh xserver-xorg

It resets the xserver to default settings so that you can get back into it.

---

### Post by onefriedrice on 2007-07-25
Thanks bigfox.  I didn't know about that command, but unfortunately it did not help my current situation.  I've also tried to boot the LiveCD, but it fails with the same issue which makes it seem like it's more than a configuration issue, unless the LiveCD is also not configured for this type of card.

I wonder if I should submit a bug report?

I attached the xorg.conf produced after the reconfigure and the log.

What do you think?

---

### Post by pxwpxw on 2007-07-25
In xorg.conf

```
Section "Device"
	Identifier	"Generic Video Card"
##	Driver		"ati"
	Driver		"fbdev"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

```
Try changing the Driver from atii to fbdev.

---

### Post by onefriedrice on 2007-07-25
Thanks pxwpxw, that did the trick, although performance was much better with the GeForce2 MX with the nv driver than this fbdev driver.  I take it fbdev is a generic works-with-everything driver and that the radeon driver just has a lot of known issues?

---

### Post by pxwpxw on 2007-07-26
> **onefriedrice said:**
> Thanks pxwpxw, that did the trick, although performance was much better with the GeForce2 MX with the nv driver than this fbdev driver.  I take it fbdev is a generic works-with-everything driver and that the radeon driver just has a lot of known issues?

Well, AFAIK fbdev is a common interface between xorg and the various video chips that support it, some dont, it doesn't work for my nvidia or intel, but it does for ati. There is a little info in man fbdev. It has some performance limitations. There is some issue with the ati driver probing the chip bios I just happen to have seen in one other case. There are some other issues with some ati chips, a search should yield results.

---

### Post by stmiller on 2007-07-26
fbdev is a framebuffer 2D generic driver. It will work fine.

Try specifying the driver as:

radeon

to try the 3D driver. But some 3D things can make your system buggy/unstable depending on which Radeon model you have.

---

