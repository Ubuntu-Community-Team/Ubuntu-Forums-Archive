---
title: "No USB at all"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by AncientMartian on 2007-02-12
Installed newest Ubuntu and everything so far works except no USB devices work or can be seen. I revived an old Pentium III 550 on a amptron motherboard (USB work under wondows with removable h/d). Ubuntu is new to me but i am used to dealing with DOS (but tis been a few years). When I checked device manager for the USB there is no unusual icon showing a problem. When i run sysinfo nothing happens. When I run Hardinfo it crashes on most things that I try to look at including USB devices. I tried typing the lsusb command on the Root Terminal but nothing is listed. The only error i have ever seen (onbootup) is something called RSPD not found but that probably doesnt have anyhting to do with this (or so I am guessing). Well thats all I was able to do on my own. I tried 4 different USB devices but none triggered anything on the computer or made any kind of reaction. There is power there for them but they dont load and I cant see them on Ubuntu anywhere (but I am not completely familuar with Ubuntu yet). I would appreciate any information that can point me in the right direction. Thanks

---

### Post by tbroderick on 2007-02-12
What are you plugging in? Plug something in (joystick or usb drive) and open a terminal. Then run;
```
dmesg
```

You should see a bunch of stuff like usbcore, ohci_hcd, ehci_hcd. At the end of dmesg you should see something similar to this;
```
input: Jess Tech USB 4-Axis 12-Button Gamepad as /class/input/input3
input: USB HID v1.10 Joystick [Jess Tech USB 4-Axis 12-Button Gamepad] on usb-0000:00:02.1-3
```

That's for my USB joystick.

---

### Post by AncientMartian on 2007-02-13
Ok, I ran that little command and I did find some information saying the USB has not been started. I am including a portion of the readout here (hopefully only the relevant portion). How to get it working?....I gues that would be my next step.

 UDMA(66)
[   41.348977] hda: cache flushes not supported
[   41.349221]  hda: hda1 hda2 < hda5 >
[   41.460635] hdc: ATAPI 63X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   41.460688] Uniform CD-ROM driver Revision: 3.20
[   41.950852] usbcore: registered new driver usbfs
[   41.952873] usbcore: registered new driver hub
[   41.962902] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   41.965097] ohci_hcd 0000:00:01.2: OHCI Host Controller
[   41.966319] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   50.233112] ohci_hcd 0000:00:01.2: USB HC takeover failed!  (BIOS/SMM bug)
[   50.233132] ohci_hcd 0000:00:01.2: can't setup
[   50.233151] ohci_hcd 0000:00:01.2: USB bus 1 deregistered
[   50.234733] ohci_hcd 0000:00:01.2: init 0000:00:01.2 fail, -16
[   50.234752] ohci_hcd: probe of 0000:00:01.2 failed with error -16
[   50.296505] Attempting manual resume
[   50.396812] kjournald starting.  Commit interval 5 seconds
[   50.396872] EXT3-fs: mounted filesystem with ordered data mode.
[   66.369141] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
[   66.859711] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[   66.859886] PCI: Found IRQ 11 for device 0000:00:0b.0
[   66.882640] eth0: Davicom DM9102 at pci0000:00:0b.0, 00:d0:09:50:18:c9, irq 1


As far as devices that I have tried include: PH 1000 Photosmart printer, a Logitech camera, memorex thumb drive, and an external harddrive. There is no software that I have tried to install for these devices other than that for the printer which currently is running thru the parallel port.       Thanks again and ready for any ideas for the next step.    -  AM

---

### Post by ir_newbie on 2007-02-17
I am kinda facing the same problem, 
i have dell latitude d500 (also second hand) ironic!?
my usb port was working fine for some time, but then suddenly both my usb ports stopped recognizing any device connected to them... i have tried with canon camera, pen drive, mp3 player... again none of these required any installation software...
are these two things connected? any help u can offer will be great...
bye
raunak

---

