---
title: "Intel Corporation 82865G Integrated Graphics Controller HELP!!!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by katxor on 2007-03-13
hi!

i just reinstalled ubuntu, since my try with the ATI graphics card didnt work im gonna give it another go.

now i need some help to update drivers for "@Intel Corporation 82865G Integrated Graphics Controller"

is there a "apt=get" way?

ie. when i scroll in firefox there is small freezes etc etc.

or is it just some tweak in xorg.conf i need to do?

btw in xorg.conf the only thing i get there is

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"

im a total newbie

---

### Post by katxor on 2007-03-13
friendly bump

---

### Post by reacocard on 2007-03-13
> **katxor said:**
> hi!

i just reinstalled ubuntu, since my try with the ATI graphics card didnt work im gonna give it another go.

now i need some help to update drivers for "@Intel Corporation 82865G Integrated Graphics Controller"

is there a "apt=get" way?

ie. when i scroll in firefox there is small freezes etc etc.

or is it just some tweak in xorg.conf i need to do?

btw in xorg.conf the only thing i get there is

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"

im a total newbie

So you want to use the intel card? or the ati? for intel open a teminal (Applications->Accessories->Terminal), copy in the following and hit enter.

```
sudo apt-get install xserver-xorg-video-i810
```
enter your login password when propmpted, hit enter for any other prompts.

then change the Driver line in xorg.conf to say "i810" instead of "vesa".

for ati, I would recommend using [EasyUbuntu]("http://easyubuntu.freecontrib.org/") to install the drivers.

---

### Post by katxor on 2007-03-15
tried it but doesnt work.
found anotherway though. i installed xubuntu then the grafic works flawless then install ubuntu-desktop on top of xubuntu

---

