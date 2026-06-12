---
title: "not able to boot from livecd"
date: 2007-05-05
forum: Apple PPC Users
---

### Post by skepticus on 2007-05-05
C key will do nothing- going to the boot menu via Option yields the livecd icon, but choosing it results in bouncing back to option screen, and need to power down to reboot.

---

### Post by Sef on 2007-05-06
1) Did you set the BIOS to boot from the CD drive before the hard drive?

2) Did you md5sum the download?

3) Did you burn the cd at 4x or less?

4) Did you check the cd if it is good or not?  (One of the options on the CD.)

---

### Post by phummers on 2007-05-07
And some maybe silly suggestions:

Is it a "new-world" mac?

[http://preview.tinyurl.com/23dg4m](http://preview.tinyurl.com/23dg4m)

And do you have more than 192 M of RAM? If not, you would need an "alternate" CD

[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

---

### Post by jolly79 on 2007-05-07
You will proberly need the ubuntu ppc alternat cd....

(there is no bios on g3 and g4 macs)

---

### Post by walter_f on 2007-05-07
> **jolly79 said:**
> 
(there is no bios on g3 and g4 macs)

There isn't a BIOS on any PowerPC Mac ;-)

Instead, there's Open Firmware.

"Old World" G3 Macs, which are _not_ able to boot from a Linux CD, are the "beige" G3 Macs (Desktop as well as Minitower), PowerBooks G3 "Wallstreet" (plus all pre-G3-Macs and older PowerBooks).

Examples for "New World" Macs (i.e., bootable from Linux CDs): iMac G3 and G4, iBook G3 and G4, PowerBook G3 "Lombard" and "Pismo", Power Mac G3 "blue /white", Power Mac G4, PowerBook G4,...

Walter.

---

### Post by Bleyze on 2007-05-27
I had the same problem with my Mac Mini. The problem was the conventional PC keyboard connected to the Mac with a Keyboard to USB converter was causing the "C" to be ignored at boot up.

Changing to a USB keyboard fixed it. 

As a test can you boot off the OS X install CD by holding down the "C" key? If you can't then it is probably the keyboard.

---

