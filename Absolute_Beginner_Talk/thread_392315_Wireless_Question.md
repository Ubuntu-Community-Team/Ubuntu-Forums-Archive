---
title: "Wireless Question"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-24
I've been trying to get my wireless connection to work for while now, but with no sucess. I have a **CNet CWP-854 PCI Card** and I can see **ra0** under the **Network Manager**, however, when I configure it and active it, Ubuntu simply won't boot next time and I end up having to re-install everything. Also, I don't know what my chipset is. When I type **lspci -n | less**, I get the following output:

```
0000:00:0a.0 Network Controller: Ralink: Unknown device 0301
Subsytem: Ralink: Unknown device 2561
```

However, when I type **iwconfig**, after **ra0** appears **rt61**. I'm not sure if this is just the driver that comes with Ubuntu, or the chipset of my card. To make things even more complicated, I don't have a ethernet connection, so I have to keep switching from Ubuntu to XP. However, I'm determined to get it to work, so please, could someone help me out?

---

### Post by .oops on 2007-03-24
If someone could help me out. My thread kinda slipped out of the 1st page. Bump.

---

### Post by .oops on 2007-03-24
Anyone?

---

### Post by eljalill on 2007-03-24
Have you tried configuring manually with iwconfig?
Not sure, whether that wouldn't have the same error as the Network Manager though...

Also I am using WiCD as a Network Manager, which works a lot better for me. Maybe you want to try it out? 
Again, no guarantee, though..

Sorry If you've tried all this already..

---

### Post by .oops on 2007-03-24
Hum, no I haven't. Could you please link me to it? Just keep in mind that I don't have a ethernet connection so it can't have lots of deps, just build-essential preferably.

---

### Post by eljalill on 2007-03-24
Well, don't think it needed a lot of .dev , but you do need wpa supplicant and such..
> 
Wicd requires python, python-gtk2, python-dbus (Edgy) or python2.4-dbus (Dapper), wpasupplicant, and python-glade2.

These will be installed automatically when you install wicd, so there is no need for you to download these manually.

 The webiste is:
[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)
And am not sure about the "automatic installation" but I don't think many can install a network manager and still be connected... at least I couldn't. :)

---

### Post by .oops on 2007-03-24
Well I tried it, it installed, but when I clicked Wicd under Applications -> Internet -> Wicd it just didn't ran. I'll try to find another network manager.

---

### Post by .oops on 2007-03-24
I got it to work. I'm in Dapper right now! I'm soo happy. :D Thanks. I'm using GTK WiFi Manager.

---

