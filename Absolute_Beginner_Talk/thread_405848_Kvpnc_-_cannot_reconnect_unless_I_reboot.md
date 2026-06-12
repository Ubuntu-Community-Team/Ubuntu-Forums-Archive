---
title: "Kvpnc - cannot reconnect unless I reboot"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by cjl2301 on 2007-04-10
I just installed Kvpnc last night and I was able to connect to my work by importing a .pcf file.  Everything works fine except if I disconnect from the VPN I cannot reconnect again unless I reboot my PC.  If I try and reconnect, it just fails.  Also, if I try and ping my vpn server, it comes back with nothing until I reboot.   I can browse the internet normally though.

It's as if vpnc is leaving my network in some kind of hosed state after I disconnect.

Any way to fix this?

---

### Post by dabbner on 2007-04-30
You could try re-starting the networking services
That will at least tell you where the issue lies, and will save you some time.  Type this into the command line.

"sudo /etc/init.d/networking restart"


I am also having issues with kvpnc/vpnc.  I get the following error connecting to all of my VPN's that worked flawlessly on 6.10.  


debug: No default interface given, tried default interface, got success, using "eth0".
info: Loading of module "tun" was successful.
debug: Using advanced settings.
info: Using UDP.
info: Trying to connect to server " <removed server name and IP for security reasons> " (***.***.***.***) with user "alex" and IPSec ID "dflt"... 
info: "vpnc" started.
info: Timeout! Kill connect process!
info: Connection failed (timeout).
info: Not connected. 


Kvpnc is running as using gksu, so priv's shouldn't cause any issues.  This is happening on three laptops for three different Fiesty users.  

Anyone have an idea why?

---

