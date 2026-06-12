---
title: "tracing wireless"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by throdon on 2007-07-27
hi i have been using *buntu since may 2007 and *buntu is the only distro i can use with wireless. matter of fact its the only distro i use beacuse no other distro i use configures my wireless. i 'am wondering how do i trace my wireless path so i can duplicate this in other distros. i'am begining to suspect it's not my hardware it's *buntu or some *buntu programe or even the kernel or dchp that is providing me with wireless. i have no hard wired internet. i only have wireless. is it my dchp, ubuntu, avahi mayby. "i don't know so if you can help me trace this I will be on my way. thankx in advance.

---

### Post by Richard Kut on 2007-07-28
From what I can tell, the e-machines t5048 is a desktop machine. Did yours come with wireless, or did you add it on afterwards? Either way, please provide the make and model of your wireless card.

---

### Post by throdon on 2007-07-29
yes my computer is a desk top. i have two(2) usb wireless G network adapters from belkin hooked up to my computer, a desktop with no wired internet. my wireless router is also belkin. 
wireless adapter model # f5d7050
wireless router model #f5d7231-4
*buntu 7.04 (dapper did not support wireless for me.)
other than that my box is a plain jane as is.
my main question is how do i trace my configuration so i might be able to duplicate within other distros.
ps. my wireless driver is listed as zd1211rw

---

### Post by Richard Kut on 2007-07-31
Hi throdon! Thanks for the clarifications. I did some poking around and it looks like your wireless adapter may be using a Broadcom chipset. In version 7.04 a.k.a. Feisty, the good folks who create Ubuntu decided to roll the Broadcom wireless drivers into the default kernel setup. Note that, although it appears to be working fine for you, the kernel driver approach does not work for everyone. It certainly did _not_ for me, and so I had to disable the kernel driver and use ndiswrapper instead.
 
Back to your original question, which is how to replicate your working wireless setup on a distro other than just *buntu. If you go to the Belkin site, then you will be able to download the Windows driver for your wireless USB unit.

[http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=0)

Now, if it is the Broadcom chipset, as I suspect it may well be, then you are in luck because the Broadcom driver for Windows will work fine in Linux as long as you wrap it using a software called ndiswrapper. There are many good guides for how to do this, written by fellow forum members, one of which is here:

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I also found a good guide for this which is specific to openSuse:

[http://en.opensuse.org/SDB:Belkin_F5D7050](http://en.opensuse.org/SDB:Belkin_F5D7050)

Lastly, I have been trying out PCLinuxOS 2007 lately, and their approach to enabling wireless is the easiest that I have seen yet. In fact, if you copy the downloaded Windows driver to a USB flash drive, and then boot with the PCLinuxOS live CD, the setup will use that driver on the USB key and do all the setup for you! Pretty neat,I would say!

I hope that some of the above helps you, and hopefully I answered your question. Please update this post with your experiences and comments. Good luck!

---

