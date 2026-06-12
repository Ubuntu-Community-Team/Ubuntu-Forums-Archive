---
title: "correct print driver for HP2100 laserjet"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-03-25
There are several (about 6 or 7) drivers listed in Ubuntu/Gutsy for a HP laserjet 2100 printer.

I tried the first one on the listing (which says recommended) and I get garbage when I print the test page.

I have the printer hooked to the LPT1 parallel port of the computer.

My question is, which of the other several drivers that are listed will give the best result with this HP laserjet 2100 setup on the parallel port, i.e. which one should I use and how would I know which one to use other than just trying them all one at a time and then what is it that will tell me that I have choosen the correct one ?

Thanks.

---

### Post by cmnorton on 2008-03-25
My experience has been that you can print to just about any HP printer. The fact you are printing garbage means you can send something to the printer. How are you configuring this printer?

As fond as I am of Ubuntu's print management -- many orders better than Red Hat Enterprise Linux's -- I am a big fan of firing up a browser and entering localhost:631. Before you do that, however, make sure you (the administrator) are also part of the lpadmin group. Then, changing the settings under Modify printer. 

Playing round with print configuration through the menus --  System Administration --> Printing -- may also work. I am just finding these days that the direct CUPS interface is better for me.

---

### Post by bumanie on 2008-03-25
Personally, I go to the HP linux site and download the self extracting installer for linux - it does all the work for you. Just check that your printer is supported first.

---

### Post by wpshooter on 2008-03-25
> **bumanie said:**
> Personally, I go to the HP linux site and download the self extracting installer for linux - it does all the work for you. Just check that your printer is supported first.

If I do that and then go into the printer setup section of Ubuntu/Gutsy, will it then have the "proper" driver on the list of available drivers for my HP2100 ?

Thanks.

P. S. - Hmmmmmmmmmmm.  Some print driver for Linux.  When I finally get to that page, and if I am correctly interpreting what it says, then MOST of the drivers that are available on that page will NOT work if the printer is running via a parallel port connection.

---

### Post by bumanie on 2008-03-25
I think you are interpreting correctly. May be a usb cable is in order and may be a pci usb hub, if you don't have any spare usb ports.

---

### Post by wpshooter on 2008-03-25
> **bumanie said:**
> I think you are interpreting correctly. May be a usb cable is in order and may be a pci usb hub, if you don't have any spare usb ports.

HP 2100 is a parallel port printer.  I don't know if a parallel port can be routed thru a USB cable but I don't think I am going to buy a cable and a hub when I have a parallel port that works fine.

Thanks.

---

### Post by ibgeorgeb on 2008-03-25
I went to System > Administration > Printing >

I selected the Laserjet-2100M choice; Manufacturer is HP, Model Laserjet 2100M, and the driver hpijs - HPLIP 0.9.7.

Using the "Connections Tab" I selected the usb://HP/Lasrjet 2100 Series. Since I'm using a usb hub.

This is only my third day of playing with Ubuntu and somehow, when I hit the "Print the Test Page," viola, out came a Ubuntu test print page. I then went to Ooo Word, used different variations of font/fonts, printed the puppy and it came out perfect.

I hope that this is the information your looking for. 

ibgeorgeb

---

### Post by worlestone on 2008-05-10
I've had the same print problems in setting up an HP Laserjet 2100 and am new to Linux/Hardy.  The recommended drivers do not appear to work -not to me anyway.  

What did work was ibgeorgeb's driver selection (HP LaserJet 2100 Foomatic/hpijs, hpijs 2.8.2)

Very happy now :-)

Thanks

---

