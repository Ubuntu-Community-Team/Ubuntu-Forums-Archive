---
title: "changing network cable, automatic new IP"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by susa on 2006-07-21
laptop has Dapper 6.06 and Kubuntu & Xubuntu

when I boot machine either at office or at home, both locations provide a dynamic IP address based on the router settings.

if I move to another desk or building without rebooting machine, it does not see the new network connection and I must reboot at new location

this is for fixed cable connections, is there a way to issue a command that automatically figures out the new IP without reboot?

---

### Post by loell on 2006-07-21
i'm not sure if this is a fix, perhaps in the network card settings whatever you desktop environment you're in, kde/gnome/xfce, try deactivating and then reactivate your lan card.

---

### Post by susa on 2006-07-21
thanks, I've done that in the past but seems like there would be a simpler way to either script it and have just a link on desktop to allow click & reset

or, perhaps there's an executable that does this?

why doesn't it work automatically ?

---

### Post by loell on 2006-07-21
i guess that's possible ;)
maybe you can request a simple script in programming talk subforum 

:)

---

### Post by stychman on 2006-07-21
Seems to me that you need to renew your DHCP and get a new IP.  In a terminal window type 
sudo ifdown eth0
sudo ifup eth0

You could also try in a terminal window typing
sudo dhclient eth0

---

### Post by jwd45244 on 2006-07-21
Try the network manager applet

---

### Post by stricevics on 2006-07-21
I agree with stychman.

To Susa:
If you just unplug the cord and plug it back in (moving the laptop to other physical location obviously doesn't matter) your wlan0 or eth0 or whichever you're using settings are still bound to the previous DHCP lease. You need to disconnect (virtually, not just physically) and then connect again in order to get new lease at DHCP server. It happens automatically when you boot your machine but you can do it manually as well.

Hope it helps.

---

### Post by geco on 2006-07-21
> **susa said:**
> laptop has Dapper 6.06 and Kubuntu & Xubuntu

when I boot machine either at office or at home, both locations provide a dynamic IP address based on the router settings.

if I move to another desk or building without rebooting machine, it does not see the new network connection and I must reboot at new location

this is for fixed cable connections, is there a way to issue a command that automatically figures out the new IP without reboot?
```

sudo dhclient eth0

```
where eth0 is your network device

---

