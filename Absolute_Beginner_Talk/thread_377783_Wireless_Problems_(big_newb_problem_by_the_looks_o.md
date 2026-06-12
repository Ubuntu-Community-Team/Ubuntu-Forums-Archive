---
title: "Wireless Problems (big newb problem by the looks of it)"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Lord Nudgesome on 2007-03-06
Hiyas, 

Although messing around with Ubuntu and other linux distros i havnt really got into it. But now i have decided to stick to it.

Im having a problem with my wireless card in my laptop, ubuntu cant find it. When installing the installer recognised the card and it was chosen as the primary network thing. But now when trying to connect, i can only find the ethernet, im not sure if its due to needing to activate it or something similar.

Please can someone help me. Thanks

---

### Post by endtroducing on 2007-03-06
Hi,

Do you have any output? You should see your adapter name if the card was detected.
If not, what type of network card do you have?

```
sudo iwconfig
```

This is an example with a 64 bit WEP key:

```
sudo iwconfig eth1 essid "WIFINET" key 1234567890
```

For help using iwconfig:
```

man iwconfig

```

---

### Post by Lord Nudgesome on 2007-03-08
Hmm... seems it isnt detected at all, its a TP-Link WN510G with a Atheros chipset i think... i might try to find a driver and ndiswrapper it instead of trying to find why it was doing it, but i swear that it was picked up during the installation.

Also another question, is there anything that needs to configured differently if the network uses a WPA code

Thanks for the help

---

### Post by endtroducing on 2007-03-08
I checked for your card and it uses the madwifi driver. **Not** ndiswrapper. And you also need wpasupplicant if you want to use WPA.

You will find plenty of information here: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

E

---

### Post by Lord Nudgesome on 2007-03-11
Ok I will try that now... thanks

---

