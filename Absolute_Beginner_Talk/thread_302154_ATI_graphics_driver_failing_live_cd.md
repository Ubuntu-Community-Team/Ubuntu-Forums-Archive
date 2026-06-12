---
title: "ATI graphics driver failing live cd?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by fatnic388 on 2006-11-18
Hi. I'm having a lot of trouble running the Live CD on my system. I think it may have something to do with my graphics card. It's an ATI Radeon Xpress 200 Series. It there any way to run the Live CD with a basic graphics mode which would perhaps bypass the default driver for my card? 

At the moment I get a line saying 'Loading...' then the screen goes blank and shows a flashing cursor. At this point the whole thing freezes. Any suggestions?

---

### Post by an.echte.trilingue on 2006-11-18
Try using safe graphics mode.

---

### Post by fatnic388 on 2006-11-18
Tried that. Exactly the same outcome. The reason I think it's my graphics card is that I've managed to install Ubuntu on a different PC. I've tried putting the HDD in my current PC but the same thing happens, even though it's already installed. Can't think what else it could be apart from a hardware issue!

---

### Post by fatnic388 on 2006-11-19
OK. I've played around with the boot options and so far I've managed to get a big list of things on my screen before it freezes. The last line I get is "Using hpet for hi-res timesource". Then nothing but the blinking cursor. What comes next and could it be stopping it from booting?

---

### Post by spandon on 2006-11-19
Hi,
I had similar problems with the Edgy (ubuntu 6.10)Live Cd on two of my machines (laptop and a desktop) both had ati cards.
I did the following to load the live cd and then to install:

**Live CD**
when the booting the disk, at the first, press escape, you will then get a message stating that you are leaving the graphical boot etc, press enter.
at the boot: prompt enter
**live vga=771 noapic nolapic** (exactly as written) and press return.
the disk then loads up edgy and I get a screen resolution of 1280x1024 plus alternatives.

If this works and you want to install, then you have to use the **Alternative CD**, and to install it, at the boot: prompt enter
**install vga=771 noapic nolapic**, then edgy installs.

This worked for me, give it a try using the Live CD, if this works then the installation will also work (using the Alt CD)
Good luck
Don

---

### Post by fatnic388 on 2006-11-19
Unfortunatly that didn't work. I it gets to the loading 'initrd.gz' part then all I get is a blank screen. Not even the flashing cursor anymore!

---

### Post by fatnic388 on 2006-11-19
Actually got it working now!!!! YES!

I had to add the line **acpi=off** in order for the Live CD to boot. However, I am now stuck with a 800 x 600 resolution. How do I go about downloading/updating the display drivers so it displays properly?

Also, when I install it will it automatically run with **acpi=off**? Sorry if these are silly questions.

---

### Post by ReaderRat on 2006-11-19
[**HowTo Resolution & Refresh**](http://ubuntuforums.org/showthread.php?t=83973)

---

