---
title: "How to add a printer to ubuntu o/s"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by chuffsy on 2008-02-15
In addition to ubuntu I also run Xp on the same computer. I use a HP printer (about 3yrs old) with xp and works fine. Now I want to be able to print when using Ubuntu...is it a simple matter of putting in the cdrom and following prompts? BTW I was not the one who installed the printer in xp. A buddy of mine did and I was not there when he did it so I am looking for assistance here as he is not available...Thanks

---

### Post by lswest on 2008-02-15
installing the printer is pretty simple, no CD required^^ now, i'm assuming it's connected via USB to the computer, so if i'm wrong, tell me^^.  Okay, so you go to system-->administration-->printing.  Then in the new window click on "new printer" it'll search for the printers connected to the PC where you can then select the printer from the list (the name of the device will be written on the top of it) and then for the driver go to HP and find the driver for the right device.  Done^^  (you can set it as default by choosing "set as default printer" when you go to system-->preferences-->default printer)

---

### Post by drs305 on 2008-02-15
Older usb HP printers of the HP 1000 vintage sometimes have problems once they are recognized by ubuntu. The problem usually is that the system sees the printer but doesn't print. If that happens, do a search on this forum by using your printer name (e.g. 1000 . 1010, LaserJet) and you can find what works for others.

I love ubuntu and don't want to dampen your enthusiasm prematurely but it may save you some time if you run into problems.

Good luck

---

### Post by bumanie on 2008-02-15
As you have a hp printer, I would go to this site [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) and download the self extracting archive with installer. HP are supportive of open source and provide good drivers. A printer of three years old should be supported (you can check under support and services elsewhere on the HP site).
As said, download the self-extracting archive to your desktop. In terminal type
> cd ~/Desktop enter
> sh hplip-2.8.2.run enter
and the installer does the rest, it just asks a few basic questions which you answer and it does all the compiling and ensures all dependencies are met. Very simple.

---

### Post by chuffsy on 2008-02-16
Thanks everyone , Im out of town for a week so when I get home I will try to add printer to ubuntu...Paul

---

