---
title: "Internal modem"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by Guy27 on 2005-07-25
I would love to ditch microsoft but I am having problems connecting to the internet. I have read a few articles on internal modems and Linux and realise I might not be able to configure my modem. However if someone could help me I would really appreciate it. I have a Agere Systems PCI Soft Modem and I am using Ubuntu with Kernal 2.6.8.1-3-386. If more information is need please ask. I live in the Queensland hinterland and only have access to Dial up.

Thank you, 

Guy

---

### Post by KrisDwyer on 2005-07-25
[QUOTE=Guy27]I would love to ditch microsoft but I am having problems connecting to the internet. I have read a few articles on internal modems and Linux and realise I might not be able to configure my modem. However if someone could help me I would really appreciate it. I have a Agere Systems PCI Soft Modem and I am using Ubuntu with Kernal 2.6.8.1-3-386. If more information is need please ask. I live in the Queensland hinterland and only have access to Dial up.

Thank you, 

Guy[/QUOTE]
 ok type 
*sudo pppconfig*
this should bring up a font and you want to create a new connection. Make sure you use the CHAP protocol.

Then when its all fine and dandy, type sudo pon to connect :)

SWEET!

---

### Post by newbie2 on 2005-07-25
[QUOTE=Guy27]I would love to ditch microsoft but I am having problems connecting to the internet. I have read a few articles on internal modems and Linux and realise I might not be able to configure my modem. However if someone could help me I would really appreciate it. I have a Agere Systems PCI Soft Modem and I am using Ubuntu with Kernal 2.6.8.1-3-386. If more information is need please ask. I live in the Queensland hinterland and only have access to Dial up.

Thank you, 

Guy[/QUOTE]
[http://www.linmodems.org/](http://www.linmodems.org/)

"Details: By definition, a winmodem is one that requires MS-Windows "engine" software to function, because it lacks otherwise-required circuitry. Some, the "controllerless" variety, are MS-Windows-dependent because they lack a controller chip (a ROM) where error correction, data compression, and modulation standards (such as V.90) would ordinarily be implemented. Thus, it is now possible, through the miracle of Conexant (formerly Rockwell) and Agere Systems (formerly Lucent, formerly AT&T) "technology", to manufacture an external  modem so brain-dead that, outside MS-Windows, it's a paperweight!"
[http://linuxmafia.com/~rick/faq/](http://linuxmafia.com/~rick/faq/)

---

### Post by ShaneR on 2005-07-25
ugh...tried for a long time to get my Agere modem working. It Would on some distros, not on others.

Ubuntu had the drivers available that you'll need.  At a prompt, type:

```
sudo modprobe lt_modem
``` 

Then,

```
sudo modprobe lt_serial
``` 

Then set up your dialer to use the proper device (/dev/ttyS*) 

*=0,1,2, or 3

That should work.

However, if you know you have the correct ttys* port specified and it still does not work, try disabling PnP in your bios...for whatever reason, that worked for me.

If after all that it still does not work, I'm afraid the best thing may be to buy an external modem off of ebay: that's what I ended up doing.

Good luck :)

---

