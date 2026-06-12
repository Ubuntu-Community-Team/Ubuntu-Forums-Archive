---
title: "Oh man , You have to be kidding.!  Do i need to un/ re-install XSane  ..?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-09-27
I've recently installed the [HP Toolbox]("http://hplip.sourceforge.net/screenshots.html") in my breezy system , It was a pain in the *** but i got it installed..

But now for whatever reason XSane can't for any reason find my scanner..

My printer is an HP PSC 1315v All-in-One printer-scanner-copier..

It worked just fine and dandy beforehand ( before i installed the toolbox ) , And now when trying to launch XSane i get the following error message:

( Error from XSane.)

**No devices available..**

***Possible reasons:***

(1) [I]There really is no device currently supported by Sane.
[/I]
(2) *Supported device's are busy.*

(3) *The permissions for the device file do not allow you to use it - Try as root.*

(4) [I]The backend is not loaded by Sane. ( man sane-dll ) .
[/I]
(5) [I]The backend is not configured correct . ( man sane-"backendname" )
[/I]
(6) *Possibly there is more than one Sane version installed..*

( Error from HP Toolbox )

*Failed to open device  hpiao:/usb/hpc_1310_series=?serial=CN464B30D402':  Error during device I/O*

WTF..????

Do i need to remove then reinstall XSane..?   if so , Where is a good download for it.? , A .deb  ?   Or in otherwords , What is the easiest way to get it..?


Now i'm irritated..

---

### Post by jason.b.c on 2006-09-27
:-k

---

### Post by maaronB on 2006-09-27
It is easy to uninstall and reinstall Xsane you should be able to do it through synaptic.

But my guess is that is not your problem.

Not that I have any idea what your problem is, but it sounds like you somehow broke your drivers when you installed the toolbox.

---

### Post by maaronB on 2006-09-27
Also the HP toolbox comes with the HPLIP drivers so it should have already been installed on your system (it was mine) it was not in any menu, but if you use alacarte menu editor it is simple to added it to the System->Admin. section.

---

### Post by jason.b.c on 2006-09-28
UPDATE

Well i tried to uninstall and then reinstall **Sane** from within synaptic manager..

It was removed and then reinstalled successfully but "It still don't work"  :mad: 

Anyone have any other suggestion's..???

How would i go about reinstalling the driver for just the scanner..???

---

### Post by maaronB on 2006-09-28
Looking through the link you [HP Toolbox]("http://hplip.sourceforge.net/screenshots.html") posted I don't see any way to download the toolbox independent of the HPLIP drivers.  So my guess is you downloaded and installed the drivers and they automatically set themselves up.

If you remeber what your old drivers were you can just go back up to 
System -> Admin. -> Printing -> click on new printer -> set it up using the old drivers -> test it -> delete other printers.

---

### Post by jason.b.c on 2006-09-28
*BUMP*   :-k

---

### Post by rajan on 2006-10-06
have you tried running as root? in my searches for a solution to my own xsane problem, i'm seeing that a lot of scanners need to be run in root unless you update a file in the udev directory as described in this thread:

[http://www.ubuntuforums.org/showthread.php?t=6419](http://www.ubuntuforums.org/showthread.php?t=6419)

good luck.

---

