---
title: "How to use printer w/OSX"
date: 2012-01-18
forum: Apple Hardware Users
---

### Post by gulmer on 2012-01-18
I have a desktop with Ubuntu 11.10, a USB printer attached. The printer is a HP Officejet 5610. Works fine with any distro. The situation is we also have an Mac PowerBook G4 w/OS X 10.5.8 laptop that I would like to also use the printer by way of our Linksys wifi router. I tried to get the Mac to connect w/the desktop through which it could use the printer. I also have a Dell D600 laptop w/Ubuntu 11.10 and have succeded to connect to the printer. If there is any Mac savy users out there that could assist with this, I would appreciate it.

---

### Post by Aearenda on 2012-01-19
If I recall correctly, doing the following on the Mac will enable Leopard to find the CUPS printer on Linux:```
cupsctl BrowseProtocols='"cups dnssd"'
```
The quotes are important here.

The issue is that CUPS (the printing subsystem) on OS X only listens to Bonjour by default, but CUPS on Linux doesn't advertise using Bonjour. This command tells the OS X CUPS to use its native protocol as well as Bonjour.

---

### Post by Q-collective on 2012-01-19
According to [this document](http://support.apple.com/kb/ht1370), there should be native support. But this support only applies with direct USB connection. If the printer is seen through USB, then it *should* also work over a network.

---

