---
title: "Cant connect to internet..."
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-08-29
With wired or either wireless. I got Ubuntu 7.04, TeleWell EA510 router. I just cant even everything should be good. Or how could I make new hdcp setting? Scince I selected not to do them on installation when it didn't work correctly (error occured always)

---

### Post by ts51 on 2007-08-29
Ok. What kind of wireless card do you have? Is it supported? What steps did you use to install it? I don't know about the wired as I am a wireless person.

---

### Post by Ozcu on 2007-08-30
Didn't do any installing. 


06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

^ Guess its that.

---

### Post by ts51 on 2007-08-30
OK. Install this: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wifi-radar](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wifi-radar)

It is called Wifi radar and it should help you connect via WiFi. If that doesn't scan and detect your radar than you may have these problems:

1) You need to install the right drivers.

2) Your not in range of your network

3) You need a new wireless card.

I'll assume the last 2 are not the problem. If WiFi radar doesn't just work, you'll need to type "lspci" (without the quotes) in the terminal and paste it hear. It will show the details of your wireless PCI card. I'm guessing you are on a desktop, but I don't know for sure because you never posted any system specs and I haven't yet perfected my Ubuntu mind and system reading powers :) 

I want to help you get Ubuntu up and runnin'. Pretty soon you will be helping others with their problems.

-ts51

---

### Post by ts51 on 2007-08-30
Sorry it took 13 hours for a reply... I'm usually more prompt but school just started.

---

