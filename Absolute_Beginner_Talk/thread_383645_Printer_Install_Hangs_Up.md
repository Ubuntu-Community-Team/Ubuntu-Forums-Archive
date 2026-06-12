---
title: "Printer Install Hangs Up"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-13
While installing printer drivers (hplip-1.7.2.run) for a HP 3600n that I just downloaded from HP, about halfway through the installation a window pops up (titled sudo). Inside the window is a DOS-like window (titled Ubuntu Configuration - Postfix Configuration) with some instructions on how the configuration can be modified following installation. I can scroll up and down in this DOS-like window using the arrow keys, but the mouse won't work in the window. At the end of the instructions there is an <Ok> area that I am assuming should be clickable or at least active when the Enter key is pressed --- nope. Can't even close the sudo window without shutting down and restarting the machine (bummer).

And still no printer driver.

---

### Post by lizzard on 2007-03-13
Try to navigate to the "OK" with the Tab-key.

---

### Post by wpshooter on 2007-03-13
My GUESS is that if you got these from the HP website that if what you download was for Linux then it is not specifically compatible for Ubuntu !!!

Printer setup in Linux in general and Ubuntu in particular still need a GREAT deal of work, IMO.

Have you tried the driver that are built into CUPS printing in Ubuntu ?

Good luck.

---

### Post by lwalper on 2007-03-13
Presto!!

Thanks.

---

### Post by lwalper on 2007-03-13
Now all I need to do is find a PPD file in step 2 of the Add a Printer dialog. Where are those stored?

---

### Post by John.Michael.Kane on 2007-03-14
You can try looking under /usr/share/ppd

---

### Post by maniacmusician on 2007-03-14
> **lwalper said:**
> Now all I need to do is find a PPD file in step 2 of the Add a Printer dialog. Where are those stored?
are you sure you actually need a PPD file? You have the HP Color Laserjet 3600n. Is that very different from the 3600? 

I see a driver listed in that list for the Color Laserjet 3600, have you tried using that driver?

one last question; during the first step, did it detect your printer, or did it say "no printers detected"?

thanks

---

