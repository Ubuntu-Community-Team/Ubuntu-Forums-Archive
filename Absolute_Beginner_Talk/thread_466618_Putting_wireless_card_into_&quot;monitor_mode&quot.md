---
title: "Putting wireless card into &quot;monitor mode&quot;"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Linux_n00b on 2007-06-06
How do I put my wireless card into monitor mode and then take it out of monitor mode?  I have a netgear WG511T wireless card (Atheros).  Help would be greatly appreciated!  Thanks!

---

### Post by esavato on 2007-06-07
```
ifconfig eth0 -promisc
```

You may have to turn the interface down before performing this task..  also, if it is a wireless card it will be iwconfig.  Check out the manpage for ifconfig for more detail...

[http://www.die.net/doc/linux/man/man8/ifconfig.8.html](http://www.die.net/doc/linux/man/man8/ifconfig.8.html)

Also check out the wire shark wiki for info on what to do once you are setup..
[http://wiki.wireshark.org/CaptureSetup/Ethernet](http://wiki.wireshark.org/CaptureSetup/Ethernet)

---

### Post by esavato on 2007-06-07
I found another great guide.

[http://www.askapache.com/security/sniffing-on-ethernet-undetected.html](http://www.askapache.com/security/sniffing-on-ethernet-undetected.html)

---

