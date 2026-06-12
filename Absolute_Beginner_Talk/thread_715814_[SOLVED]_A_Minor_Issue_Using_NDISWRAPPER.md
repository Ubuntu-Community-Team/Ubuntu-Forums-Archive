---
title: "[SOLVED] A Minor Issue Using NDISWRAPPER"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2008-03-05
Hi all,

I have just successfully setup my Belkin USB adaptor with windows drivers using ndiswrapper. The only small thing is that it shows "no network connection" in the Gnome GUI, next to the date. Is there anyway of controlling it from there or does it need to be done  at the command line. I inputted the SSID, WEP key etc in System>Admin>Network?

Thanks

---

### Post by MikeJ112 on 2008-03-05
Also I have just rebooted and it is still working, so it seems it will reconnect to my WLAN after a reboot, just want to know if I can change it using the the network facility

---

### Post by MikeJ112 on 2008-03-08
I think I might have answered my own question: if I type:

```
su gedit/ etc/network/interfaces
``` and then # the beginning of all lines except auto lo & iface lo inet loopback NetworkManager will then be able to take control of my Wifi adaptor. I'm reading the "beginning ubuntu" book btw :lolflag:

---

### Post by MikeJ112 on 2008-03-08
> **MikeJ112 said:**
> I think I might have answered my own question: if I type:

```
su gedit/ etc/network/interfaces
``` and then # the beginning of all lines except auto lo & iface lo inet loopback NetworkManager will then be able to take control of my Wifi adaptor. I'm reading the "beginning ubuntu" book btw :lolflag:

I'm unable to do it at the moment as I am at work

---

### Post by timbounceback on 2008-03-08
I don't know if it will work, but I do know that it should at least be:```
sudo gedit /etc/network/interfaces
```

---

### Post by MikeJ112 on 2008-03-08
> **timbounceback said:**
> I don't know if it will work, but I do know that it should at least be:```
sudo gedit /etc/network/intefaces
```

Ah yes, thats right! Has anyone else had problems with NetworkManager & NDISWrapper?

---

### Post by timbounceback on 2008-03-08
aha, found something [here]("http://ubuntuforums.org/showthread.php?t=190747")

---

### Post by MikeJ112 on 2008-03-08
Ive just installed KWiFiManager and all is fine now, thanks

---

