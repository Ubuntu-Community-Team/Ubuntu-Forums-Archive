---
title: "USB Printing to Airport Extreme from Linux - HELP!"
date: 2006-09-02
forum: Apple PPC Users
---

### Post by greggfathead on 2006-09-02
Hello - My home wi-fi network is all Apple hardware based - an Airport Extreme base station and four Airport Express repeaters connected to various stereos and/or printers throughout my house. I did this so that I could stream iTunes to any stereo in the house from any computer, and so far it works perfectly. No issues conecting my Ubuntu laptop to the Airport network, it's working perfectly!

However - my Ubuntu laptop cannot print to the printers at all, the printers are USB-connected to the Airport Express access points. The Macs access the printers via Bonjour, but I cannot figure out how to get the Ubuntu machine to print to these printers! Can someone help me with this?

Note: the Airport Express access points get their IP's dynamically from the router, however I could set these IP's to be static if need be. Maybe that will solve the issue?

Does anyone know how I can set up my Ubuntu box to see those printers? I've tried using my Unix Printer (LPD) setup and naming the Apple hardware to which the printer is attached, but no such luck - no printing magick happens.

I did find this resource about how to print from XP to my Airport Extreme-attached printers: [http://www.ifelix.co.uk/tech/1004.html](http://www.ifelix.co.uk/tech/1004.html) - but who wants to use XP?  :)  I'd rather use Ubuntu, and besides - I blew the XP partition away a while ago on my PC.  I'll try to convert these instructions from PC to Linux, but I would appreciate any help any one could offer.

** [Note: I posted this in the General Support area last week and no one replied, so I thought I'd re-post in the Mac-centric forums to see if anyone here had any insight.  I'm running Ubuntu on both a Gateway laptop (only running Ubuntu, no XP partition) and on a 12" iBook G4 (dual booting in Ubuntu/OSX 10.4) ].

Take care, and have a great day!

---

### Post by lodp on 2007-02-07
i'm a little late to reply, but did you get this to work? i haven't got any experience with Apple hardware, but i've got an Asus WL-500g Premium router with USB. You'll definitely have to set the station with the printer attached to a static IP, and the print to that IP from Ubuntu (just install a new printer, select TCP/IP, and enter the IP-address of the Airport Ex. with the printer). I don't know whether you'll have to select RAW printing. On my router, it works fine with the regular printer driver.

i'm very curious as to whether you managed to stream music to the Airport Express  --  how would you do that?  My Asus router runs on linux -- I plugged a cheap USB-sound card, installed the eSound daemon on the router, and now i can stream to it, using kmplayer.

---

### Post by AlphaMack on 2007-02-07
Just use your AirPort's IP number (i.e. 10.0.1.1, 172.16.1.1, or 192.168.1.1) and enter either port 9100 or 9101 (if one doesn't work, try the other).  Make sure to select HP JetDirect.

---

### Post by lodp on 2007-02-11
how about audio output, though? how do you get that? i don't suppose the AirPort Express runs the eSound daemon...

---

### Post by AlphaMack on 2007-02-11
No audio output for the AX unfortunately.  Apple use a proprietary encrypted stream.  Of course, if someone out there can reverse engineer the encryption.......but then again Apple will just do what they did with DAAP and their iTMS user keys.

---

### Post by bunkenburg on 2007-02-25
This works for me: [http://ubuntuforums.org/showthread.php?t=156675](http://ubuntuforums.org/showthread.php?t=156675)

---

### Post by svenand on 2007-03-06
Here is a description on how to print to an Airport Express from Linux.

[http://svenand.blogdrive.com/archive/14.html](http://svenand.blogdrive.com/archive/14.html)

---

### Post by buffalo2001 on 2007-11-16
> **bunkenburg said:**
> This works for me: [http://ubuntuforums.org/showthread.php?t=156675](http://ubuntuforums.org/showthread.php?t=156675)

Thank you so much...I followed the directions to a T and this worked great!

---

