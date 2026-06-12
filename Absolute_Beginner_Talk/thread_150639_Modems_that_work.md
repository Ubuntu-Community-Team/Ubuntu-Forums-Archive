---
title: "Modems that work?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by kayla on 2006-03-26
Could someone please suggest a modem that will give me the least amount of trouble to setup? Make and model# would be great. Kind of hard to try out ubuntu when you can't get online. I'm trying to use the 64 bit version of breezy. Thank you.

---

### Post by CallsignBaron on 2006-03-26
dial-up, cable or dsl?? Need to be more specific.

---

### Post by eriefisher on 2006-03-26
Internal or External???

---

### Post by Ian Maxwell on 2006-03-26
Do you mean dialup modems? Your safest bet is a controller-based modem--it requires no drivers, as it handles everything in hardware. An eBay search for "controller-based modem" should get you what you're looking for.

---

### Post by Bartender on 2006-03-27
kayla - 
You still there?
I picked up a couple of US Robotics Sportster 0701's (these are external, serial port) on Ebay for about $20 each when all was said & done.  Using the Windows side of the machine, I went to USR's support site and downloaded the installer package to update the firmware.  Booted up in Ubuntu and Ubuntu recognized the modem no sweat.  I enabled it in - um - Administrator > Networking I think.

Lots of directions in past threads for using the various dial-up programs available in Ubuntu.  I think there are at least three different ways to control a modem.  I used Modem Monitor.

My ISP (Juno) doesn't work with Ubuntu so I haven't been able to verify functionality, but the modem chirped and bleeped and appeared to dial Juno.  One little complication - there are a series of tiny dipswitches on these hardware-based modems and I haven't found any directions for setting them.  Fortunately, mine appears to be working with the switches where they are.

---

### Post by akiro.yamamoto on 2006-03-27
If your referring to dial-up modems....
If you have an available serial port, you can use an external serial modem.
These are supported by default.
I've also had good results with the Intel 537EP modem. Intel provides drivers for it 8)
You can also check [** LinModem !!! **]("http://linmodems.org/")
for drivers for supported windows modem that you can use with Linux.
Hope this info helps ;)

Edit:
This is the modem I'm using..... ;)
[** Best Data 56SX92 **](http://www.gearxs.com/gearxs/product_info.php?products_id=3464)

---

### Post by jason.b.c on 2006-03-27
> Could someone please suggest a modem that will give me the least amount of trouble to setup? Make and model# would be great. Kind of hard to try out ubuntu when you can't get online. I'm trying to use the 64 bit version of breezy. Thank you.

I found on the internet that a **U.S. Robotics 5610b** internal modem is supported by linux..:)     Although i've had no experiance with this modem, so i can't back that up. :( 

It would be awsome though if it does work with ubuntu...:)

---

### Post by kayla on 2006-03-27
Wow, lots of traffic on this board, had some trouble finding my original post. 
Yes, dialup. I don't care either internal or external. 
I was looking at a us robotics 5686E, external. [http://www.newegg.com/Product/Product.asp?Item=N82E16825104135](http://www.newegg.com/Product/Product.asp?Item=N82E16825104135)
Was hoping someone had one, or could at least say they thought it would work properly. 
Thanks!

---

### Post by frank392 on 2006-06-29
Hi Kayla 
the best modem you can guet for Linux is a Modem blaster external V.92 Model DE5621 it is a serial modem do NOT get the usb modem. and you can use JUNO OR NETZERO. they work graet with Linux I posted The solution at: mepislovers 
[http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=15025&forum=9](http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=15025&forum=9)

if you need more help let me know

have fun 

Frank

---

### Post by darthchaosofrspw on 2006-07-23
> **kayla said:**
> Could someone please suggest a modem that will give me the least amount of trouble to setup? Make and model# would be great. Kind of hard to try out ubuntu when you can't get online. I'm trying to use the 64 bit version of breezy. Thank you.

My Conexant HSF-based modem works great here on Ubuntu. You just have to download the Linuxant driver that matches the OS (Ubuntu) and the Linux kernel your Ubuntu system has (for me, I had to download hsfmodem_7.47.00.01full_k2.6.15_23_386_ubuntu_i386.deb.zip because my Linux kernel (when using uname -r in the console) is 2.6.15-23_386. Unfortunately, Linuxant drivers require a one-time fee so it doesn't fall under the "free as in beer" definition.

---

### Post by jason.b.c on 2006-07-23
This one works for sure..!  I'm using it right now..!

[Creative Modem Blaster v.92]("http://us.creative.com/products/product.asp?category=7&subcategory=40&product=52")

:D

---

### Post by prost on 2007-01-10
Would would the PCI version of the Creative Modem Blaster V.92 work?

I do have an old serial v90 modem(1998).
I'm planning to use xandros Linux.

---

### Post by Peter6218 on 2007-06-05
> **kayla said:**
> Wow, lots of traffic on this board, had some trouble finding my original post. 
Yes, dialup. I don't care either internal or external. 
I was looking at a us robotics 5686E, external. [http://www.newegg.com/Product/Product.asp?Item=N82E16825104135](http://www.newegg.com/Product/Product.asp?Item=N82E16825104135)
Was hoping someone had one, or could at least say they thought it would work properly. 
Thanks!

This is what I use. Works perfectly on Xandros V3 Linux and two flavours of Windows. So far I've been unable to get Ubuntu 7.0.4 to either recognize it or use it. 

Can anybody help??

---

