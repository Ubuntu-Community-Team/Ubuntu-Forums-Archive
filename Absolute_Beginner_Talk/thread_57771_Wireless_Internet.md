---
title: "Wireless Internet"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-08-17
I just installed Ubuntu on a computer which I run Linux and Windows on.  I have a wireless card (Linksys) that seems to work (and was easily detected) on Windows, but not on Ubuntu.  I have basic cable internet, but I cannot seem to configure my wireless card.  Any suggestions?

Thank you.

---

### Post by Brunellus on 2005-08-17
[QUOTE=apmcavoy]I just installed Ubuntu on a computer which I run Linux and Windows on.  I have a wireless card (Linksys) that seems to work (and was easily detected) on Windows, but not on Ubuntu.  I have basic cable internet, but I cannot seem to configure my wireless card.  Any suggestions?

Thank you.[/QUOTE]
 your wireless card's driver might not be supported by Linux...

A table of wireless cards, chipsets, and degrees of functionality can be found in the wiki:  

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)

---

### Post by amcavoy on 2005-08-17
Thanks for the reply.  So if it isn't supported, there isn't any way around it?

Thanks again.

---

### Post by Nequeo on 2005-08-17
There sure is!

Follow the steps on this page:
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

You might get lucky... If your card does work after following those instructions, and the model number is listed on the compatibility list, let us know so it can be added.

Cheers,

---

### Post by cosmarium on 2005-08-18
[QUOTE=Brunellus]your wireless card's driver might not be supported by Linux...

A table of wireless cards, chipsets, and degrees of functionality can be found in the wiki:  

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)[/QUOTE]
  I have a similar problem. I can't navigate from ubuntu. I have incorporated wireless. What can I do?
thanks

---

### Post by amcavoy on 2005-08-20
I set it up so my that my wireless card was external, then I plugged it into the computer with ethernet and it worked perfect.  It might not be the most efficient way, but it worked.

---

