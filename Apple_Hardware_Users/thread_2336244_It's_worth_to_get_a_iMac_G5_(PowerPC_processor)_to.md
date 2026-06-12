---
title: "It's worth to get a iMac G5 (PowerPC processor) to run Ubuntu 16.04 with Unity Deskto"
date: 2016-09-06
forum: Apple Hardware Users
---

### Post by instantware on 2016-09-06
I would like to get a iMac G5 to have a beautiful and compact computer to my home. I will use it to do the following tasks:

* Developing Java and PHP applications (NetBeans, LAMP Package and OpenJDK)
* Use the multimedia center software (Kodi)
* Browse the internet (Latest Firefox or Chromium Browser)
* Watch YouTube (May be using HTML5 viewer or Minitube software) and Netflix (The latest Chromium Browser is compatible)
* Edit Photos with GIMP
* Use native Skype with Webcam (Ancient versions for PowerPC were discontinued for Mac OS) and it's avaiable only in x86 builds for Linux.


This computer will be a very cheap option to have a all in one computer. Something like US$ 100 in perfect state. Here in Brazil, a newer 
computer like an Intel Core i3 iMac is very expensive and my needs are not so much demanding. Now i would like to know
some things, since i already used the Ubuntu 9.04 when i had an iBook G4 in 2010. 

I would like to get this computer: 

Apple iMac G5/2.0 20-Inch (ALS) Specs

Processor Speed: 2.0 GHz / PowerPC 970* (G5) 
Video Card.....: Radeon 9600

1) Is the Radeon driver for Ubuntu 16.04 capable enough to run the Unity Desktop flawless?
2) Is possible to run x86 binaries using some tweak that enables x86 emulation using native Linux without need to emulate
an entire operating system to get it like an x86 subsystem in PowerPC Linux?
3) Is this computer fully compatible with latest Ubuntu version?

---

### Post by rican-linux on 2016-09-09
I would not use Unity at all on a PPC Mac. It is just too resource intensive. I would suggest either Lubuntu or Ubuntu-MATE.

---

### Post by chdrsto on 2016-09-09
Or you wait for some time (until the new macOS Sierra is available) ... all iMac's before "late 2009" will be affordable for less money.

---

### Post by luigiburdo on 2016-09-09
> **chdrsto said:**
> Or you wait for some time (until the new macOS Sierra is available) ... all iMac's before "late 2009" will be affordable for less money.

Imac G5 ... cant run lastest osx .... leopard and stop.. apple crappy

---

### Post by luigiburdo on 2016-09-09
* Developing Java and PHP applications (NetBeans, LAMP Package and OpenJDK)

YES it can and do 

* Use the multimedia center software (Kodi)

YES it can and do 


* Browse the internet (Latest Firefox or Chromium Browser)

YES it can and do 

* Watch YouTube (May be using HTML5 viewer or Minitube software) and Netflix (The latest Chromium Browser is compatible)

YES it can and do with firefox ... only no flash is available max 720p because 1080p is slow because va vdapu are crappy


* Edit Photos with GIMP

YES it can and do 


* Use native Skype with Webcam (Ancient versions for PowerPC were discontinued for Mac OS) and it's avaiable only in x86 builds for Linux.

No it can not ... no skype for linux ppc 


1) Is the Radeon driver for Ubuntu 16.04 capable enough to run the Unity Desktop flawless?

Can but mesa are not optimized 

2) Is possible to run x86 binaries using some tweak that enables x86 emulation using native Linux without need to emulate
an entire operating system to get it like an x86 subsystem in PowerPC Linux?


Quemu user ... but noting is using it ... qemu-system-x86 is slow ... performance like a x86 700mhz on g5 2.5ghz
VirtualPC (osx) performances on G5 2.5 ghz in integer like P4 3.0ghz like P4 700mhz in fpu


3) Is this computer fully compatible with latest Ubuntu version?[/QUOTE]

yes it is .

---

### Post by chdrsto on 2016-09-10
Hi luigi

I'm talking about x86 iMacs.

---

### Post by ernsteiswuerfel on 2016-09-10
@[instantware]("https://ubuntuforums.org/member.php?u=622306"):
16.04.1 LTS has its flaws, especially with an r300-card, which the Radeon 9600 is. You will have a much smoother experience with 16.10 or you could wait 'til the 4.8.x kernel and mesa 12.0.x hit **16.04.2 LTS**.

---

