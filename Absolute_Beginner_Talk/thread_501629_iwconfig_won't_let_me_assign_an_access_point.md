---
title: "iwconfig won't let me assign an access point"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-15
I've just got my hardware running etc etc etc 
I've manually added the network name and encryption key to /etc/network/interfaces and the values show up when I type iwconfig, but I can't seem to assign an access point. The command 'sudo iwconfig wlan0 ap XX:XX:XX:XX:XX' doesn't give any errors, but it just doesn't do anything! Nothing happenes when I add it to /etc/network/interfaces (I add wireless-ap XX:XX:XX:XX:XX) but the output of iwconfig is still Access Point: Not-Associated
Does anyone know why and what I can do?
(oh I'm on Orange broadband with a Wanadoo Livebox)
Thanks!

---

### Post by ukripper on 2007-07-15
try wlassistant, it is kde app but you can run in gnome from cli. Easy to configure essid.

```
sudo apt-get install wlassistant
```

---

### Post by rjfioravanti on 2007-07-15
Try 

```

sudo iwconfig wlan0 essid <ap name>

```

then see if the AP is set

if not, do

iwlist scan

and see if the ap shows up somewhere, if not then you cant see it

---

### Post by tartarian on 2007-07-15
I'm running Xubuntu, but I've no internet connection. Wireless is my only hope! :(
And yes i've done that and it set the essid, but I had already specified it in my interfaces file, so I'm not sure if it did actually modify it or what :(

---

