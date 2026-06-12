---
title: "Network almost set up; how do I set it up to connect at boot?"
date: 2008-12-24
forum: Arch and derivatives
---

### Post by Redrazor39 on 2008-12-24
Ok I have my /etc/tc.conf set up so that all I have to do to connect to my wireless network is:

```
dhcpcd wlan0
```
Idk if I sudo or not. 

How do I set it up so this is run at boot and I can get straight online?

EDIT: I already followed the beginners guide and installation guide to the letter, so please don't suggest that. I probably just don't understand something and I need it to work.

---

### Post by Rumor on 2008-12-24
[http://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_Management](http://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_Management)

Scroll down to the bit about editing your /etc/rc.conf file and put in the appropriate settings and you should be all set.

---

### Post by Redrazor39 on 2008-12-24
I did all that a while ago but I still have this problem. I'm not sure what to do :(

---

### Post by OutOfReach on 2008-12-24
I think it would be easier to use a daemon like WICD.

---

### Post by namegame on 2008-12-24
> **OutOfReach said:**
> I think it would be easier to use a daemon like WICD.

Here's the wiki page for it:

[http://wiki.archlinux.org/index.php/Wicd](http://wiki.archlinux.org/index.php/Wicd)

I used WICD for quite a while, but have since moved to configuring my network via CLI.

---

