---
title: "HP 1020 USB Printer Won't Print"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by happyisland on 2007-02-05
Hello Ubuntu community,
I just bought a new computer for my business (an HP 1020 usb printer). The install process looks like it goes fine, but when I print a test page nothing happens. 

I searched around for an answer, and tried to use hp-toolbox. When I start that I get the following errors:

HP Linux Imaging and Printing System (ver. 1.6.9)
HP Device Manager ver. 6.2

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
warning: No status available for device.


Any help on this one would be much appreciated.
Thanks,
Happyisland

---

### Post by emarkay on 2007-02-05
Very strange - I had this last night on my PSC-1350.  

Hmmm, I just checked Spaceweather and Seesat, no solar flares or Chinese ASAT tests recently...  :)

I just reinstalled HPLIP and all was well - didn't even need to recreate printer configs.

Make sure you are using the latest version, 1.7.1
[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)

MRK

---

### Post by happyisland on 2007-02-05
Weirdest thing is, now I can't download the hplip 1.7.1 - it keeps stalling my browser (I've tried both Mozilla and Firefox). What is this all about?

---

### Post by Spr0k3t on 2007-02-05
You should check out the drivers created by Rick Richardson.  With his help, he created a driver setup for the KonicaMinolta I have.

[http://foo2zjs.rkkda.com/forum/list.php?7](http://foo2zjs.rkkda.com/forum/list.php?7)

Highly recommended and deserves our support for all the work he's done so far.

---

### Post by happyisland on 2007-02-07
Many thanks to both emarkay and Spr0k3t for the advice. I was finally able to manually install the hplip 1.7.1 (by following the instructions on their site after the automatic installer failed to work) and now the printer is working! 
Thanks to you both, and to this great community.
-HI

---

