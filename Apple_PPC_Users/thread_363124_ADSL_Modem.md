---
title: "ADSL Modem"
date: 2007-02-16
forum: Apple PPC Users
---

### Post by centaur78 on 2007-02-16
Hi

I have just installed Ubuntu on my old iMac G3 and it works perfectly.... I now have an ADSL connection, but the ethernet port of this iMac burned out long back and i would like to connect using the usb....

the problem is the USB drivers for the ADSL modem ( its a UTStarcom ADSL 2+ UT300R2U)
provided by the isp is i486 based of linux.... is there anyway i can port this drivers to the Ubuntu ppc version.....

Or is there anyother way i can get this to work ???
:( 

thanks in advance

---

### Post by beanworks on 2007-02-17
Sort of a Rube Goldberg solution, but you could try wireless:

Get a USB wireless adapter (one that is supported by MADwifi would be a good choice)
Get a wireless router (preferably one with which the USB adapter is compatible):) 

Set up the router and modem using a computer that has a working ethernet port (once it is set up, you don't need the ethernet connection any more).  
Plug in the USB adapter before you turn on the iMac.  It should be automatically detected by Ubuntu, although you will have to go into the Networking tool to configure the wireless connection and to make sure the ethernet connection is disabled.

---

