---
title: "canon ip5200r"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by figi22 on 2008-01-20
I have two printers for my computer, an HP PSC750, which works fine, but the Canon ip5200r does not work.  If I try to print then everything looks like it's working (says printing in progress) but nothing happens.

If I try to print a test page then I get this message: "There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Is this due to the problem with Canon not providing Linux drivers, or is it something else?

---

### Post by bwtranch on 2008-01-20
Your going to have to go get a driver and configure it. I wish you luck. The first place to start is the OEM website. This is the last place to look.

---

### Post by figi22 on 2008-01-20
I wasn't sure what you meant by OEM, but found it on Wikipedia.   

I looked on the Canon website and they have a few Linux drivers but not one for ip5200r, so I registered my interest in them developing one.  

I thought about downloading the ip5000 one to see if that would do, but got a bit stuck just downloading the manual.:(

I just wondered if anyone else had developed anything.  I thought this community might be able to help as it's a very popular printer.

---

### Post by bumanie on 2008-01-20
Essentially, canon are not supporters of open source and thus don't provide many drivers. If canon have a driver for the 5000 version, try it, it is probably close enough and will most likely work.
What is the problem you are having with the canon manual? If you direct someone to the website, they may be able to help you.

---

### Post by AndrewRodaway on 2008-07-03
A bit late, but I have just successfully printed via WLAN to my Canon Pixma iP5200r. I just installed it first as a USB printer using the CUPS+Gutenprint v 5.0.2 driver and did a test print OK. Then made a copy of the printer and changed the device URI in the settings dialog to socket://192.168.1.101 which I know to be the IP address of the wireless interface and it just worked... (yes, I did pull out the USB cable first...)

a.

---

### Post by Wilburight on 2008-07-21
Not too late - I've been hanging out for this development. Now to get it to print onto CD/DVD disks - which is what I mainly use it for. I guess that's a job for Canon or their software creators though :(

---

