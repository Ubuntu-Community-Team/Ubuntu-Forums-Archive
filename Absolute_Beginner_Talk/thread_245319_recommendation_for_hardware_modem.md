---
title: "recommendation for hardware modem"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by ahilde on 2006-08-27
I've searched the threads, but don't seem to see what I need.  I am using a Dell with Windows 2000 and a Conexant winmodem.  I'd like to find a hadware modem that Linux will recognize so I can get on line and then begin to learn my way around Ubuntu and Linux.  I am completly  new to Linux, but am determined to get away from Windows.  Got any recommendations for a dial-up modem?

---

### Post by ieee488 on 2006-08-27
I'd be interested in this too.

But my friend who uses Fedora recommends buying an external serial modem - not USB one though. You can usually find some used ones on eBay.

---

### Post by ahilde on 2006-09-09
I bought a Robotics Sportster on ebay.  Seems to be OK.  Unfortunatly I still can't reach the isp.  Dialing seems to go OK, but no registration on the network.

---

### Post by ieee488 on 2006-09-09
I am still waiting for the external modem that I bought on eBay. :(

The internal modem I have is recognized by Ubuntu.
It's a US Robotics that came with my Dell that I bought in 2000.
It has the TI chipset. How lucky was I!!! :D 
It is an OEM modem sold to companies like Compaq and Dell.

My company recently was going to throw out a modem from an old PC that it had lying around. And guess what, it was another one of the US Robotics modem with the TI chipset. It will be my back-up.

You should be able to get an internal one for about $10-12 on eBay. Look very carefully at the photos and the model numbers.

A large but incomplete list of PCI modems and Linux
[http://www.devidal.tv/~chris/winmodems/pci_list.html](http://www.devidal.tv/~chris/winmodems/pci_list.html)

---

### Post by ieee488 on 2006-09-09
> **ahilde said:**
> I bought a Robotics Sportster on ebay.  Seems to be OK.  Unfortunatly I still can't reach the isp.  Dialing seems to go OK, but no registration on the network.

For my ISP, they use CHAP authentication. Some use PAP.
Ask them which one they use.

---

### Post by Omnios on 2006-09-09
> Hi my dad has a Smartlink es 2838 2839 modem. With Ubuntu 5.10 his port was port 14 and he tryed to set it up using his old port to connect which did not work. Anyways after doing some problem solving I got him to run the following command in the Terminal.
     Code:
     [LEFT] $ sudo wvdialconf /etc/wvdial.conf[/LEFT]
  
 
 Which told him the modem was now on port 4, after figuring this out his modem worked again without the addition of any extra drivers.

 Basicly when we set up his dial up we ran wv to get the port number input the port into the network dial up from menu and it just worked no drivers needed

---

### Post by ahilde on 2006-10-04
My Robotics Sportster is now working fine and I have another on the way.
In wvdia.conf I had to set init = atz4.  After that everything went smooth.

---

