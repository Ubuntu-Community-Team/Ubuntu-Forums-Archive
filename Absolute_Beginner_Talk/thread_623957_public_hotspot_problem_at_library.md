---
title: "public hotspot problem at library"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by BakaGaske on 2007-11-26
okay, right now i'm using my gf's macbook to post this.

I"m in a public library trying to access the internet with Ubuntu. HAL (or whatever is recognizing the wifi connection) says that i'm connected and i even have an ip address. The library is using IPv4 (don't know if that's important), and the connection is open. The problem, when i open swiftweasel, i get "page cannot be found". It's not required to login, but I have to agree to the terms set out by the library and press "I agree" and i "connect"

So right now, I'm stuck. My wireless card is an Atheros AR2413. I installed madwifi last night, but i don't know how to configure cause, you know, i'm a newb.

So if there's any help out there, much appreciated.

Thanks

---

### Post by Dr Small on 2007-11-26
Did you connect to the wireless network ?
Maybe you could try restarting network:
```
sudo /etc/init.d/networking restart
```

It does the trick for me some times.

Dr Small

---

### Post by zach12 on 2007-11-26
Yes the library's network doesn't work 
and they told me that my computer wasn't compatibil with ther wifi and to come back when i  use windoz:confused:

---

### Post by moore.bryan on 2007-11-26
> **zach12 said:**
> Yes the library's network doesn't work 
and they told me that my computer wasn't compatibil with ther wifi and to come back when i  use windoz:confused:
*that's garbage... i'm sure there's a way around it.  are you using network-manager or wicd for your connections?*

---

### Post by BakaGaske on 2007-11-26
Umm let's see. I'm using the default network manager that comes with Gutsy. But I don't get what's the problem cause my university's wifi requires me to log on through a web browser, but it's WEP encryption. Would that be the reason? The fact that the library's wifi is open?

---

