---
title: "How do I make Ubuntu recognize my modem?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Captain Chaos on 2007-02-19
Hey, I installed Ubuntu in an old PC a few days ago but can't make it go online. I found linmodems.org but the website is a bit frustrating. It'd be appreciated if anyone could guide me step by step.

Thanks.

---

### Post by teaker1s on 2007-02-19
firstly what make and model is your modem, is it 56k/ISDN/ADSL EXTERNAL USB OR INTERNAL PCI

---

### Post by Captain Chaos on 2007-02-19
[IMG]http://i22.photobucket.com/albums/b348/falsehopesgg/untitled.jpg[/IMG]

---

### Post by moore.bryan on 2007-02-19
[I]the genica website says windows only and there's no genica listing on linmodems.org... 
to share a little about my linmodem/winmodem ordeal... i specifically bought a linmodem for it's linux support and couldn't get it running on ANY distro.  it offered me a nice reason to upgrade to cable internet...
[/I]

---

### Post by teaker1s on 2007-02-19
okay so we have a 56k pci modem. the issue becomes what chip the card uses so we can find a driver-as your indicating modem not recognized in networking.
please look at black chip on modem and tell us any details written on it , also any model details printed on the card

On desktop panel click
applications > accessories > terminal

please type this command and post output
[COLOR="Red"]lspci[/COLOR]

small L not i

subscribed to thread please post details requested and I will be back to reply again

---

### Post by doobit on 2007-02-19
Any hardware modem (Rockwell, or Hayes compatible) will work. The Winmodems need specific, proprietary, Windows software to complete the modem. There are Linux solutions for some, but not all of them.

---

### Post by Captain Chaos on 2007-02-19
Can anyone recommend me a modem that will work fine with Ubuntu then? I might switch to cable internet in a few months.

---

### Post by Captain Chaos on 2007-02-19
> **teaker1s said:**
> okay so we have a 56k pci modem. the issue becomes what chip the card uses so we can find a driver-as your indicating modem not recognized in networking.
please look at black chip on modem and tell us any details written on it , also any model details printed on the card

On desktop panel click
applications > accessories > terminal

please type this command and post output
[COLOR="Red"]lspci[/COLOR]

small L not i

subscribed to thread please post details requested and I will be back to reply again

Give me a few minutes to hook everything. So heres what it says:

SmartLink
SL1801
XHFJLJ00000A

---

### Post by Captain Chaos on 2007-02-19
I'm using images because Its easier than typing everything.
[IMG]http://i22.photobucket.com/albums/b348/falsehopesgg/untitled2.jpg[/IMG]

---

### Post by ieee488 on 2007-02-19
Personally, I'd start with using ScanModem tool.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by teaker1s on 2007-02-19
> **ieee488 said:**
> Personally, I'd start with using ScanModem tool.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

according to google your modem the "smartlink smartpci563" is supported and the wiki page should get you going

---

### Post by Captain Chaos on 2007-02-19
Can you link me to it?

---

### Post by teaker1s on 2007-02-20
[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

---

