---
title: "Can't Connent To Internet -- Redetect?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by daynah on 2005-11-30
My dad has unplugged my networking cord to the router and then repluged it back in. Now Ubuntu wont connect to the internet. Is there a way to ask it to redetect the internet connection like it did while installing?

Also, because of [another problem]("http://www.ubuntuforums.org/showthread.php?t=96391"), I can't use any browser other than Konquerer, though that's not the main thing I use the internet for.

---

### Post by Robgould on 2005-11-30
Ubuntu will try to detect your network connection every time you boot, so you should be able to reboot.  I don't know how you are set up, but you will want to make sure that you are using dhcp or fixed on both ends.  If your router changed IP addresses and you do not have dhcp going, that might be your issue.  Another option is to configure your router to always give your computer tye same ip (static).
 
You should be able to got system administration --> networking and try to activate your connection from there.  You can also click on properties and check your IP configuration. 
 
Good luck.

---

### Post by daynah on 2005-11-30
Is it supposed to be eth0? Not a bigger number?

---

### Post by Robgould on 2005-11-30
eth0 is correct.

---

### Post by daynah on 2005-11-30
everything seems to be the same between ubuntu networking and the router. I'm unable to assign static IPs since it would mess with too many other computers (9).

Literally, every time I boot this computer, a new problem pops up. This time is that it hangs on "Waiting for Network interface to come up" which, to silly me, sounds somehow related. Sometimes, though, it instead takes a long time on "Configuring network interfaces" but does get through.

EDIT: Tried it with the live cd. Firefox works (ha) but this time with the live cd, the internet also isn't working. In network connections, the ethernet wasn't even configured. When I tried what I thought would be the correct setting (DHCP, since that's what the router says), it still doesn't like me.

---

### Post by daynah on 2005-12-01
All solved! We disconnected every cord that connects the two computers and the computers to the internet and reconnected them and reset everything, and all was fine. Now whether or not that actually helped or I had something plugged in wrong to begin with is a mystery.

---

### Post by Robgould on 2005-12-01
Glad you are up and running.

---

