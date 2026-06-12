---
title: "help me"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by FlyinRedneck on 2007-06-25
I completely installed my wireless using ndiswrapper. I got it working with:

Sudo depmod -a
sudo modprobe ndiswrapper

then i made sure it would start on boot with:

sudo ndiswrapper -m

but when i restarted it wouldn't work anymore. it was even blinking! It wasnt under the network!

i entered the command 

ndiswrapper -l 

I got 

athfmwdl - driver installed
netwpn11 - driver installed

Device 1385:5f01 present

so i decided to unplug it and plug it back in.

the computer froze completely. so, i restarted it. this time i never got a single blink from my wireless adapter.

so:

i entered the command 

ndiswrapper -l 

I got 

athfmwdl - driver installed
netwpn11 - driver installed

and that is it.

when i quickly recovered the boot log i found this:
-------------------------------------------------------------------
Jun 25 11:40:20 Pixel-Popper kernel: [   29.444000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Jun 25 11:40:20 Pixel-Popper kernel: [   29.664000] usb 1-2: reset full speed USB device using uhci_hcd and address 3
Jun 25 11:40:20 Pixel-Popper kernel: [   29.848000] ndiswrapper: driver netwpn11 (NETGEAR,09/26/2005,1.5.0.2102) loaded
Jun 25 11:40:20 Pixel-Popper kernel: [   30.588000] ndiswrapper (miniport_init:275): couldn't initialize device: C0000001
Jun 25 11:40:20 Pixel-Popper kernel: [   30.588000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
Jun 25 11:40:20 Pixel-Popper kernel: [   30.588000] ndiswrapper (miniport_halt:339): device d98c0400 is not initialized - not halting
Jun 25 11:40:20 Pixel-Popper kernel: [   30.588000] ndiswrapper: device eth%%d removed
Jun 25 11:40:20 Pixel-Popper kernel: [   30.588000] ndiswrapper: probe of 1-2:1.0 failed with error -22
Jun 25 11:40:20 Pixel-Popper kernel: [   30.640000] usb 1-2: USB disconnect, address 3
Jun 25 11:40:20 Pixel-Popper kernel: [   30.680000] usbcore: registered new interface driver ndiswrapper
Jun 25 11:40:20 Pixel-Popper kernel: [   30.884000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Jun 25 11:40:20 Pixel-Popper kernel: [   31.052000] usb 1-2: configuration #1 chosen from 1 choice
-----------------------------------------------------------------------------------------------

What did i do wrong? What do i do now?

---

### Post by Seisen on 2007-06-25
Once you reboot if you do sudo modprobe ndiswrapper it should work

---

### Post by FlyinRedneck on 2007-06-25
i have tried that.

---

### Post by Seisen on 2007-06-25
Which wireless card is it?

---

