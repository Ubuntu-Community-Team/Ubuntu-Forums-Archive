---
title: "usbvision svideo problems"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by beninburgh on 2007-04-22
I am trying to get an old Hauppaugge WinTV USB card to work:

lsusb gives:

Bus 001 Device 003: ID 0573:4d32 Zoran Co. Personal Media Division (Nogatech) Hauppauge WinTV-USB III (PAL) FM Model 573

modprobe -l | grep usbvision gives:

/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/usbvision/usbvision.ko

I've tried installing tvtime, xawtv, kdetv, zapping, vlc and gxine without any luck in any of them except for xawtv, and zapping which can give a black and white picture. I'm only using the composite video input to the card, which I remember having problems in the past when using an earlier version of ubuntu. Unfortunately I didn't make any notes.

uname -r gives

2.6.20-15-generic

Can anyone help with this? I've got the cvs sources for usbvision, and have altered the default SwitchSVideoInput to 1 (as I remember this working in the past), but when I try to compile them, this happens:

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/ben/usbvision/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ben/usbvision/src/i2c-algo-usb.o
/home/ben/usbvision/src/i2c-algo-usb.c:223: error: unknown field &#8216;slave_send&#8217; specified in initializer
/home/ben/usbvision/src/i2c-algo-usb.c:224: error: unknown field &#8216;slave_recv&#8217; specified in initializer
make[2]: *** [/home/ben/usbvision/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/ben/usbvision/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

I am using Feisty.

I'd appreciate any hints,

Cheers,

Ben

---

### Post by beninburgh on 2007-04-24
Ok, This problem was solved in some manner, or at least understood by reading this page:

[http://en.wikipedia.org/wiki/S-Video](http://en.wikipedia.org/wiki/S-Video)

If anyone else has this problem, there is a way to get the software to do it, as windows displays colour images fine, but the fastest way to get it to work for me anyway in ubuntu was to stick a bit of metal between pins 3 and 4 of the S-Video connector. Or to put a 470pF capacitor in series with pin 4, as described here:

[http://www.epanorama.net/circuits/svideo2cvideo.html](http://www.epanorama.net/circuits/svideo2cvideo.html)

Although I haven't tried this yet.

I'm not sure whether the Switch is not working in the usbvision module, or simply that I don't know how to use it. Which is more likely.

---

