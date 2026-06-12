---
title: "Television through DVI Port"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by mrnyce87 on 2008-03-15
I have recently acquired a Samsung LN-T5265F television, and it's great. Up until a few days ago I was using Windows Vista's Mobility Center to connect my laptop to my television (through my VGA port) and was able to use it to watch videos, display images and the like. Is there a way that Ubuntu can do this easily? The television has a native resolution of 1920x1080.

As for my laptop:

Product Name 	dv1660se
US Product Number 	ET732UA#ABA
Microprocessor 	1.66 GHz Intel® Centrino® Duo mobile technology featuring Intel® Core™ Duo processor T2300
Microprocessor Cache 	2MB L2 Cache
Memory 	1024MB 533MHz DDR2 System Memory (2 Dimm)
Memory Max 	2048MB
Video Graphics 	Intel Graphics Media Accelerator 950
Video Memory 	128MB (shared)
Hard Drive 	80GB (5400RPM) SATA Hard Drive
Multimedia Drive 	LightScribe 8X DVD±RW and CD-RW Combo Drive with Double Layer Support
Display 	14.0” WXGA High-Definition BrightView Widescreen Display (1280 x 768)
Fax/Modem 	High speed 56k modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 	Intel® PRO/Wireless 3945ABG Network Connection
Sound 	Altec Lansing
Keyboard 	101-key compatible

2 Quick Launch Buttons (HP Quick Play Music and DVD buttons)
Pointing Device 	Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad
PC Card Slots 	

    * 1 ExpressCard/54 Slot (also supports ExpressCard/34)

External Ports 	

    * 3 Universal Serial Bus (USB) 2.0
    * 2 headphone-out
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 TV-Out (S-video)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 Expansion Port 2, 1 IEEE 1394 Firewire (4-pin)
    * 1 Consumer IR (Remote Receiver)


I'd appreciate any help I could get in solving this problem. Thanks.

---

### Post by gobbles414 on 2008-03-15
mrnyce87,

Try this procedure:

1. Go *System => Administration => Restricted Drivers Manager* and enable the driver for your graphics. If there's not an option for your graphics in that window, then you might already be using the best Linux driver for your hardware.
2. Turn your computer off.
3. Connect you computer to your TV.
4. Boot your computer and log into Ubuntu. If this fails, skip to step A.
5. Go *System => Administration => Screens and Graphics* and adjust the resolutions for both of your screens as needed.
6. Restart Ubuntu and then go *System => Administration => Screens and Graphics* again. Confirm that your resolution settings are stable.

A. Connect your TV to your computer.
B. Do you get a GRUB menu as your computer boots asking if you want Ubuntu or XP? If not, press the escape key on your keyboard as your computer is booting. Otherwise, allow your computer to start booting normally.
C. In GRUB, choose the *Rescue Mode* for your highest kernel version.
D. You computer will boot to a command line interface. Type *sudo dpkg-reconfigure xserver-xorg* and press enter on your keyboard.
E. Follow the instructions in the wizard. When you're done, type *sudo reboot* and then press enter. Boot normally and log into Ubuntu.
F. Go *System => Administration => Screens and Graphics* and adjust the resolutions as needed.
G. Restart Ubuntu and then go *System => Administration => Screens and Graphics* again. Confirm that your resolution settings are stable.

Does this help?

---

