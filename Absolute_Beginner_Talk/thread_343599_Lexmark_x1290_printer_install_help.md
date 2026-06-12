---
title: "Lexmark x1290 printer install help"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-21
my lexmark x1290 is recognized and the default driver is for the 1100 so im like...well ok

but i dont  know what to put for the device location, it is a local printer on usb port 1 

but i cant get it to print.



thanx

---

### Post by userundefine on 2007-01-21
If it's recognized when you plug it in (you can found out by plugging the USB in, and then after typing "dmesg | tail" in a terminal -- if you see information about your printer, it's recognized), then it should show up shortly after and give you a device location.

About getting it to print... there may be hope, you may just be using the wrong driver.  According to [LinuxPrinting]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x1290"), it should work perfectly.  But, that page recommends using the Z600/Z601 driver, so try that !

You're lucky, I guess.  I tried to get a Lexmark working recently but it was totally unsupported and was unfortunately a paperweight.

---

### Post by ndworecki on 2007-01-23
dmesg | tail isnt showing anything about my printer

---

### Post by oilchangeguy on 2007-01-23
have you completed the steps to install it? as far as the location, local means the printer is attached to this computer, network means the printer is attached to another computer, and is shared over the network.

---

### Post by ndworecki on 2007-01-25
i installed it but it asks for device loaction and its on usb but i dont know what to write

---

### Post by s3phiroth on 2007-03-23
Try this tutorial i compiled: [http://www.trodrigues.net/wiki/linux:ubuntu:lexmark_x1290](http://www.trodrigues.net/wiki/linux:ubuntu:lexmark_x1290)

The location you refer to, if it is the location on the third dialog it's not a location on your computer, but a description of where the printer is located (like home, office, whatever). Many people are confused by that.

---

### Post by Feenix3k on 2007-03-25
> **s3phiroth said:**
> Try this tutorial i compiled: [http://www.trodrigues.net/wiki/linux:ubuntu:lexmark_x1290](http://www.trodrigues.net/wiki/linux:ubuntu:lexmark_x1290)

The location you refer to, if it is the location on the third dialog it's not a location on your computer, but a description of where the printer is located (like home, office, whatever). Many people are confused by that.

This is the setup I used to get my Dell A920 to work with Ubuntu. But for some reason it will not work in 6.10. I do the directions but the z600 does not show up under Lexmark printers

---

### Post by s3phiroth on 2007-03-25
You sure you installed the driver by hand ?

Anyway, i already got rid of my Lexmark, got a refund and bought a HP Deskjet F370 for 2 Euros less :D

---

