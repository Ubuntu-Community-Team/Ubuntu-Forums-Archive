---
title: "list of ubuntu-compatible dialup modems?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by manipura on 2006-08-11
i've been reading many hours to find a compatible modem, and i don't want to waste money on one that won't work. 

isn't there a list somewhere of modems that work out of the box with ubuntu, kubuntu, xubuntu, edubuntu?

---

### Post by editrix on 2006-08-11
[http://start.at/modem](http://start.at/modem)

Which I found by going to: [http://linmodems.org/](http://linmodems.org/)

Which I found by Googling "Linux modems."

---

### Post by ferebee on 2006-08-11
> **manipura said:**
> i've been reading many hours to find a compatible modem, and i don't want to waste money on one that won't work. 

isn't there a list somewhere of modems that work out of the box with ubuntu, kubuntu, xubuntu, edubuntu?

The site Editrix mentioned is a good place to start.

External Serial Modems seem to be compatible with most Linux distros, so one of those is usually a safe bet. I've got a
US Robotics Courier modem that has worked with every distro I've tried out. 

External serial modems can be quite expensive new, but if you've got access to Ebay or similar you can get a used one at a reasonable price.

---

### Post by vodsonic on 2006-11-26
I am a big fan of the U.S. Robotics V.Everything Courier Business Modem. It's a big, external serial modem that is to modems what the Ford F250 is to pickup trucks. The Hardware Guys recommend it as the best modem money can buy. If it doesn't work with your Linux distro, there's something wrong with your distro.

List price is really high (US$200?) but you can get used ones on eBay all the time for a small fraction of that price. Just make sure you buy one with a power supply included, as they have a proprietary connector (I think). 

The power supplies themselves are also strange - when you plug the wall-wart in, the DC end doesn't show any power when you put a volt meter across it. But plug it into the modem it's designed for, and you've got power. I've mistakenly thrown at least one USRobotics power supply away after testing it with a volt meter and thinking it was dead.

And, yes, it works more or less out of the box with Ubuntu. To set it up, follow the instructions here: 
[https://help.ubuntu.com/community/DialupModemHowto/HardwareModem](https://help.ubuntu.com/community/DialupModemHowto/HardwareModem)

and here:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6)

If you use 'Alternate Way 1' to set up your dialer, you can then start wvdial from the command line, or install gnome-ppp, kppp, or another graphical interface to control it. (Actually what you need to do is 'sudo wvdial' - without sudo, it didn't work for me.)

---

### Post by wpshooter on 2008-06-23
> **editrix said:**
> [http://start.at/modem](http://start.at/modem)

Which I found by going to: [http://linmodems.org/](http://linmodems.org/)

Which I found by Googling "Linux modems."

This start.at/modem link seems to lead to nowhere !!!

---

### Post by carolus on 2008-06-24
"serial modems" seem to be specified for linux dial-up, but current computers no longer have a serial port.  Is there no USB modem that is equivalent?  Do you need both a USB-to-serial converter and a modem with serial input, or does "serial modem" have some other meaning?

---

