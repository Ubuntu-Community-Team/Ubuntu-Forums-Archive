---
title: "[SOLVED] Is this hardware compatable?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-05-15
Is there support for this?
[http://www.pcconnection.com/ProductDetail?sku=7031791&SourceID=k40132](http://www.pcconnection.com/ProductDetail?sku=7031791&SourceID=k40132) (specs below)

 -----------------------------------------------------------------------
Audio Output Form Factor 	External
Audio Output Interface Type 	USB
Audio Output Mode 	5.1 channel surround
Performance 	 
Sample Rate (maximum) 	48 kHz
Contents 	USB SoundWave Optical 5.1, USB cable, fiber optic cable, documentation
Ports/Connectors 	(1) USB 1.1
(1) Toslink optical output
(1) Analog output: 2-channel analog stereo
Power Notes 	Operating current: 90mA (max)
System Requirements 	Pentium III 450MHz or equivalent PC with an available USB port
Windows 98SE / ME/2000/XP/Server 2003
128 MB system memory or above
5.1-channel speaker system required for 5.1-channel sound effects
Warranty - Labor 	5 Years
Warranty - Parts 	5 Years
---------------------------------------------------------------------------

It says Windows, but that has never deterred me. I cannot test it on my system, because I do not yet have the new laptop coming in to place right by said system. Of course, Ubuntu 7.06 is the OS of choice.

---

### Post by annda on 2007-05-15
i wouldn't get my hopes up too high.

where do you live? what i mean is: can you test the device and return it if it's not OK with linux?

---

### Post by AAM on 2007-05-15
agree with annda

try to get a trial device and plug in.

have you searched on the net for answers ("linux +device")?

---

### Post by chamberlain2006 on 2007-05-15
And btw, your message says 7.06, which doesn't exist.  Feisty is 7.0**4**

---

### Post by rouge568 on 2007-05-15
Nope, I already bought it, and off ebay, so no returns.  #-o #-o
I'll test it out when I get the laptop.

---

### Post by Rhubarb on 2007-05-15
I think there's a good chance it'll work.

[http://www.alsa-project.org/](http://www.alsa-project.org/)
It says there "All USB devices that are standards compliant will work. If they do not please report to the mailing lists. If your USB device is not on this list yet here are some generic install instructions.    [usb-audio]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=USB&card=Generic&chip=Generic&module=usb-audio")"

I'm the proud owner of a Hercules USB DJ console (mark 1, not mark 2), it is essentially a 6 channel USB sound card with lots of nobs on it.
[http://www.hercules.com/showpage.php?swcty=UK&p=127&b=0&f=0](http://www.hercules.com/showpage.php?swcty=UK&p=127&b=0&f=0)
The analogue and digital optical sound works fine and instantly works when you plug it in.

The only problems that I can see that you may have with the unit you've bought, is that it encodes Dolby Digital / DTS data to fit 6 channels on one TOS link line.  That is probably done in hardware, though there's a chance it's done in software.  If it is done in software, then it'll probably only do 6 channel output in windows.

Atleast the unit you've bought isn't too expensive, so if it doesn't work, it's not a big loss.

---

### Post by rouge568 on 2007-05-15
thanks for the optimism. :)
nice system

Update: yes, it works! However, I have to have it plugged in during boot or it won't come through the USB cable.

---

