---
title: "low wifi strength atheros card, update drivers?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Unreal223linux on 2007-06-16
I have a toshiba l35 laptop and everything pretty much works great but my wifi strength is pretty terrible. It takes forever to connect unless I'm sitting next to the router. On windows I could walk all over my house and even go outside on the porch or deck and still get a connection. 

On ubuntu I can barely go two rooms away and it will be buggy, disonnecting, ect.
How do I know what kind of wireless card I have(I know its atheros), how do I figure out which version of mad wifi I'm using, and how do I update madwifi?

Thanks.

---

### Post by crispy_420 on 2007-06-16
The atheros cards just connect slow, that is how they are. That is the nature of the driver.

As far as updating, check the products home page. 

Sorry I couldn't help more.

---

### Post by ugm6hr on 2007-06-16
> **crispy_420 said:**
> The atheros cards just connect slow, that is how they are. That is the nature of the driver.

Errrmmm.  Not true for all Atheros cards.  Mine (5005G) works just fine with madwifi driver and Wicd on any network (and worked fine with Network Manager with open/WEP networks).

To find out which Atheros card you have:
```
lspci
```
Look for "Network Controller"

It is worth ensuring that you have the Atheros Restricted Driver activated (check in System->Restricted Driver Manager).

I have heard that some Atheros cards work better with ndiswrapper - just find your card chipset in the ndiswrapper wiki
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by Unreal223linux on 2007-06-16
I'm not worried about how long it takes to connect, I'm worried about connection strength. If I'm sitting in the same room as the router then everything worked fine but when I went upstairs to sit at the kitchen table or on the couch it could barely hold a connection(it would connect, work a few minutes and then disconnect). Wifi is the main reason I even have a laptop so I had to dump linux and put xp back on. :(

Maybe I"ll try again when the drivers improve.(I was getting so close! My sound finally worked but I just cant have buggy internet connections)

Thanks for the help.

---

### Post by ugm6hr on 2007-06-16
> **Unreal223linux said:**
> I'm not worried about how long it takes to connect, I'm worried about connection strength. If I'm sitting in the same room as the router then everything worked fine but when I went upstairs to sit at the kitchen table or on the couch it could barely hold a connection(it would connect, work a few minutes and then disconnect). Wifi is the main reason I even have a laptop so I had to dump linux and put xp back on. :(

Do you use WPA? If so - then this is a known problem with madwifi / Network Manager.  Try wicd (version 1.2.9) instead.

[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

EDIT: The Launchpad report for this bug:
[https://bugs.launchpad.net/network-manager/+bug/37821](https://bugs.launchpad.net/network-manager/+bug/37821)

---

### Post by jimrz on 2007-06-16
> **ugm6hr said:**
> Do you use WPA? If so - then this is a known problem with madwifi / Network Manager.  Try wicd (version 1.2.9) instead.

[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

really?  ...  I have two laptops, each with different cards but both using atheros 5212 chipset, and have had no problems on either one connecting to any of several wpa-psk ap's. maybe you should check and see if you need to update your card's firmware

---

