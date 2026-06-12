---
title: "Ultimate dialup modem"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by moilzpoil on 2006-11-12
Is there on the market today a hardware modem, usb or pci that requires 

no driver?  Seems like there would be a market for such device.  If so,

who carries it,  who makes it.

---

### Post by autocrosser on 2006-11-12
Well-I bought a Smartlink PCI modem from a vendor on eBay for 9.99+shipping--took about 1/2hr to get the drivers & set it up--had a little trouble moving to Edgy (had to update the driver), but it works very well for me--there is a very good HowTo on the forums to set-up;)

---

### Post by loell on 2006-11-12
buy safe? external dial-up modems are always compatible with linux

---

### Post by moilzpoil on 2006-11-12
I,m away from home for a month and have access to high speed. At home it

 is dialup only.  Been working with three modems at home and have one usb and

 one pci modem to the point where they dial out but don't connect.  I WILL 

keep at it until I get it figured out. Have read that in the past modems were

 made that were hardware only, no drivers to install. If this were still the 

case, it seems that a person would be reading more about it. And of course 

life would be easier for noobz!

---

### Post by Midway on 2006-11-12
That is, SERIAL external modems are always safe.  USB externals do not work too well with Linux.

---

### Post by Bartender on 2006-11-12
Go on Ebay and look for the old US Robotics serial externals.  That's assuming of course you have a serial connection.  The 5686 models.  Make sure it's not a really old 28 or 36K.  You want the 56K models, then you can hook it up to a Windows PC and go to USR's website to flash the firmware to the latest version.  The black ones are newer than the beige ones.  
There were no drivers for the external, just opened up the Networking tab, gave it the phone #, password, etc. then added Modem Monitor to the panel.  Open Modem Monitor, click Activate, and it dials.  My ISP, Juno, kinda sucks and kicks me off after a half hour, and the Linux PC isn't as fast as the Windows PC.  I'd like to hear from some other dial-up folks about their experiences with ISP's!
Also the US Robotics PCI 5610's oughta work.  I haven't tried one but would like to.

---

### Post by moilzpoil on 2006-11-12
New HP 820 without serial ports. Used a usb to serial adapter to make a zoom modem  dial out, but being a minimalist, less is more. Every step you don't have to take is time and energy saved.  Nothing learned either, of course.:mrgreen:

---

### Post by autocrosser on 2006-11-12
And if you can find one-- Zoom 2986L USB modems are hardware USB--no drivers--modem is identified as a /dev/ttyACM0 (I have one as a spare--always hooked good--it's 56K, but normally hooked as 38-42K)

---

### Post by moilzpoil on 2006-11-12
Thanks, everyone.  I'm going to keep working on the softmodem setup, it was just going slow trying to dialup on one computer to get to the repositories and download and transfer to the other machine. Got a month of high speed access here before its back to snail speed.

---

