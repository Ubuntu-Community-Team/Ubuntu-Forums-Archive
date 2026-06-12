---
title: "Apple TV"
date: 2007-08-13
forum: Apple Intel Users
---

### Post by asmith3006 on 2007-08-13
Hi
The Apple TV was hacked quite a while ago to run full OSX, does anyone know if it will work with bootcamp and let me install Ubuntu on it? Sounds like a great lounge computer to me if it does :)

Andrew.

---

### Post by 67comet on 2007-08-14
I'm not sure about Ubuntu getting the green light but I do remember reading the guys that got Mac OS X fired up called it a success but lacked several functions like Internet, 3D video and something else. But it did run, just not with all the bells and whistles.

Hope they get'r going though, I keep waling by the Apple TV and wanting to pick it up. Cheap is neat.

Justin

---

### Post by randeepjalli0 on 2008-02-28
there is a tutorial for gentoo, but i dont know how easiily it could be ported to ubuntu, apparently, most if not all of the hardware already works with the drivers either being in the kernel(nouveau) or in the repos(nvidia-restricted), I think it is important to note that 3D ACCELERATION WORKS!!!!!!. Past that, it shouldnt be too hard to get the wifi working, it is apparently some kind of a broadcom card(not much experience with that), 

From The Article:

```

Intel HD Audio

    * HDA-Intel driver recognized by default
    * Analog RCA - WORKING (see http://forum.awkwardtv.org/viewtopic.php?f=23&t=167&hilit=&start=70)
    * Optical SPDIF - WORKING
    * HDMI - apparently NOT WORKING 

irDA interface

    * mactel-linux driver recognizes it - untested otherwise
    * first signal from apple remote is somewhat recognized. Any following signals are not reported. After reloading usbhid module another signal is reported (using cat with /dev/input/by-id/usb-Apple_Computer,_Inc._IR_Receiver-event-ir) 

patch appleir.c to include the AppleTV IR USB id (#define USB_DEVICE_ID_APPLE_TV_IR 0x8241) in the same way as USB_DEVICE_ID_APPLE_IR and it will work.

    * Apple_TV_Linux_IR_Howto details the userspace method. 

Broadcom BCM94321MC wireless

    * NDISWrapper Windows drivers - WORKING with a Dell Driver and ndiswrapper 1.41 


USB

    * USB booting works when you disable ehci-hcd in kernel
    * possible to boot Linux from USB Flash memory?
    * USB HID working (keyboard, mouse), but not with ehci-hcd
    * USB Storage working (tested with usb memory stick), but not with ehci-hcd 



```


Link to the article:

[http://wiki.awkwardtv.org/wiki/Linux_on_Apple_TV]("http://wiki.awkwardtv.org/wiki/Linux_on_Apple_TV")

:guitar:

---

### Post by haxor999 on 2008-05-19
Anyone looking to get Ubuntu running on the apple tv should really look at [http://code.google.com/p/atv-bootloader/]("http://code.google.com/p/atv-bootloader/"). 
The associated wiki and mailing list of the project explain everything that's needed to get Ubuntu (Hardy or Gutsy) running - with all hardware working (except sound over HDMI and possibly hibernation).

---

