---
title: "Clueless beginner, many problems."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Questionmarktarius on 2007-10-27
Here's the system specs:

Compaq Presario 7360 (circa 1999)
AMD K62 500Mhz
504MB available RAM (8MB taken by really bad integrated graphics)
Gusty Ubuntu

Big ol' list of problems:
* Dinosaurically old bios gives me some sort of APCI=force warning.  I have no idea what this means.
* Both HD's (10GB, 80GB) are invisible to the 'computer' window.
* mad screen flicker
* i've no idea where bash is hiding.
* USB ports appear to be dead.

My intent was to rid myself of windows 98 and use the venerable machine as a LAN NAS and print server.  With the HDs and USB just plain gone, this isn't working out well

---

### Post by gn2 on 2007-10-27
My advice would be to get the Alternate CD of Xubuntu 7.04.

I had similar problems with a P3 500mhz laptop and 7.10, just couldn't get it to run properly.

---

### Post by Questionmarktarius on 2007-10-27
So the alt will probably be better for me than the full?

---

### Post by Martje_001 on 2007-10-27
> **Questionmarktarius said:**
> So the alt will probably be better for me than the full?
Well Xubuntu is Ubuntu, but with another window manager, (and maby better old hardware support?)

---

### Post by gn2 on 2007-10-27
> **Questionmarktarius said:**
> So the alt will probably be better for me than the full?

It's more likely that the difficulty is 7.10 rather than the CD type, my P3 500mhz laptop runs 7.04 perfectly.

The Alternate CD usually works better in my (limited) experience.

It's actually very simple to use the 7.04 Alternate CD.
Boot the CD, then select the "Install a command-line system" option.
The installation process is  roughly the same as the installer in the Live CD.

Eject the CD, re-boot, log-in, insert the CD and enter "sudo aptitude install xubuntu-desktop"
(substitute ubuntu-desktop if using the Ubuntu Alternate CD)

Re-boot and you'll (hopefully) have a working system.

---

### Post by Questionmarktarius on 2007-10-27
> **gn2 said:**
> It's more likely that the difficulty is 7.10 rather than the CD type, my P3 500mhz laptop runs 7.04 perfectly.Ah.
I'll roll back and see what happens.  thanks.

---

