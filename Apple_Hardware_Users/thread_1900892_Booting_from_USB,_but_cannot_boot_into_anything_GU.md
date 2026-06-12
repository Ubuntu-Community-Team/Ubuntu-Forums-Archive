---
title: "Booting from USB, but cannot boot into anything GUI"
date: 2011-12-27
forum: Apple Hardware Users
---

### Post by allenbina on 2011-12-27
Hey All,

Just for some background, I successfully have ubuntu booting from usb without refit on my hd.  I'm using a strange method of putting the ubuntu image (as .iso) in a folder and using some hacky method I found listed on a few forums here and there.  Ultimately, I thought I had failed, but after rebooting a few times I finally turned my volume up and noticed I'm hearing the welome chime.  I can get into tty2 by the familiar ctrl+alt+funciton+f2 and even checked to make sure the ethernet is working.

I can see the ubuntu logo and the loading balls underneath it and at a certain point I hear the login sound and the screen doesn't change.  I can get into a terminal and ethernet works as well but I don't know how to add whatever packages need to be added to get past the issue I'm having.  I assume its a drivers issue but I don't know how to get past that.

Any advice?

---

### Post by 2F4U on 2011-12-27
Some info on your hardware and in particular your graphics card would be helpful.

---

### Post by allenbina on 2011-12-27
Welcome to forums 101, sorry about that. 

I have the Nvidia model from late 2010 with the inbuilt intel graphics and the 330M
I also have the upgraded screen resolution and matte finish, although I don't think the matte finish makes a difference, I'm pretty sure I'll need to change my resolution manually in any xorg settings.

macbook pro 6,2
2.4 ghz i5
8gb memory


Intel HD Graphics:

  Chipset Model:	Intel HD Graphics
  Type:	GPU
  Bus:	Built-In
  VRAM (Total):	288 MB
  Vendor:	Intel (0x8086)
  Device ID:	0x0046
  Revision ID:	0x0012
  gMux Version:	1.9.21
  Displays:
Display Connector:
  Status:	No Display Connected



NVIDIA GeForce GT 330M:

  Chipset Model:	NVIDIA GeForce GT 330M
  Type:	GPU
  Bus:	PCIe
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	NVIDIA (0x10de)
  Device ID:	0x0a29
  Revision ID:	0x00a2
  ROM Revision:	3560
  gMux Version:	1.9.21
  Displays:
Color LCD:
  Resolution:	1680 x 1050
  Pixel Depth:	32-Bit Color (ARGB8888)
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Built-In:	Yes
Display Connector:
  Status:	No Display Connected

---

