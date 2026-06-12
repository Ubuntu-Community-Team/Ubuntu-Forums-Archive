---
title: "PC-BSD WUSB54GC (rt73 ralink) Wifi Help"
date: 2008-05-05
forum: BSD
---

### Post by gamergod131 on 2008-05-05
I am interested in running the latest pc-bsd on my system, however I have had no success in getting my linksys wusb54gc(rt-73) when I installed it, and Google has been no help to me. The device, it seems, is not even detected in the network setup utility for kde(the name escapes me at the moment). :(

P.S.-Please be patient, as a long time windows user, I am still new to the GNU/Linux and BSD operating systems.

---

### Post by cardinals_fan on 2008-05-05
I have a Belkin adapter which also uses the rt73 chipset.;  It works GREAT on *BSD with minimal effort.  Try the following in a terminal (you have to be root - enter 'su' and your admin password).  Then enter 'ifconfig'.  If you see an entry for 'rum0', type the following (each line is a seperate command):
```
ifconfig rum0 up
ifconfig rum0 ssid 'enter your network ssid here'
dhclient rum0
```
If this doesn't work, try 'man rum' for help.  I think that PC-BSD includes the rum driver... if not this whole thing is void.

EDIT: OK, it looks like only the development release of PC-BSD currently includes the rum driver (mini-rant: why did PC-BSD insist on splitting so far away from FreeBSD, making it harder to upgrade to 7.0-Release, which would include this!).  This is bad news for you, but it should be possible to install rum anyway.  I'll look...

---

### Post by gamergod131 on 2008-05-06
> **cardinals_fan said:**
> I have a Belkin adapter which also uses the rt73 chipset.;  It works GREAT on *BSD with minimal effort.  Try the following in a terminal (you have to be root - enter 'su' and your admin password).  Then enter 'ifconfig'.  If you see an entry for 'rum0', type the following (each line is a seperate command):
```
ifconfig rum0 up
ifconfig rum0 ssid 'enter your network ssid here'
dhclient rum0
```
If this doesn't work, try 'man rum' for help.  I think that PC-BSD includes the rum driver... if not this whole thing is void.

EDIT: OK, it looks like only the development release of PC-BSD currently includes the rum driver (mini-rant: why did PC-BSD insist on splitting so far away from FreeBSD, making it harder to upgrade to 7.0-Release, which would include this!).  This is bad news for you, but it should be possible to install rum anyway.  I'll look...

Thanks for responding :)

---

### Post by agim on 2008-05-06
I have been interested in using pc-bsd myself. Can anyone tell me if it runs with a livecd?

---

### Post by cardinals_fan on 2008-05-06
The only real chance I see here is using ndiswrapper to install the Windows drivers for your card.  If that doesn't work, you can wait until PC-BSD releases a new version based off FreeBSD 7.0.

---

### Post by gamergod131 on 2008-05-06
> **cardinals_fan said:**
> The only real chance I see here is using ndiswrapper to install the Windows drivers for your card.  If that doesn't work, you can wait until PC-BSD releases a new version based off FreeBSD 7.0.

Ughh, the windows drivers for this card are abysmal...I'll wait for a new version. Thanks though.

---

### Post by myusername on 2008-05-06
I am interested in bsd...can anyone tell me what the best bsd distro is that supports this card?

---

### Post by cardinals_fan on 2008-05-07
> **myusername said:**
> I am interested in bsd...can anyone tell me what the best bsd distro is that supports this card?
NetBSD, OpenBSD, FreeBSD, and DragonFlyBSD all should support this card in their latest versions.  Be aware that these sytems require a bit of effort.  The easier to set up BSDs, such as PC-BSD and DesktopBSD, should support this in their next release (based off of FreeBSD 7.0).

---

### Post by Iandefor on 2008-05-09
> **cardinals_fan said:**
> I have a Belkin adapter which also uses the rt73 chipset.;  It works GREAT on *BSD with minimal effort.  Try the following in a terminal (you have to be root - enter 'su' and your admin password).  Then enter 'ifconfig'.  If you see an entry for 'rum0', type the following (each line is a seperate command):
```
ifconfig rum0 up
ifconfig rum0 ssid 'enter your network ssid here'
dhclient rum0
```If this doesn't work, try 'man rum' for help.  I think that PC-BSD includes the rum driver... if not this whole thing is void.

EDIT: OK, it looks like only the development release of PC-BSD currently includes the rum driver (mini-rant: why did PC-BSD insist on splitting so far away from FreeBSD, making it harder to upgrade to 7.0-Release, which would include this!).  This is bad news for you, but it should be possible to install rum anyway.  I'll look...Wouldn't adding```
ifconfig_rum0="DHCP"
```to /etc/rc.conf work, too? Works fine for my ath card.

---

### Post by cardinals_fan on 2008-05-09
> **Iandefor said:**
> Wouldn't adding```
ifconfig_rum0="DHCP"
```to /etc/rc.conf work, too? Works fine for my ath card.
Yes.

---

