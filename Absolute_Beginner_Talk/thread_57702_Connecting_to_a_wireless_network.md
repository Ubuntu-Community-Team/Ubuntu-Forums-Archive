---
title: "Connecting to a wireless network"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by AsburyPark on 2005-08-17
I need help connecting to my wireless network.  My card works (iwlist eth1 scan), it shows my network.  I have set my AP and Essid.  I just think I'm missing a step in here.  

```
 iwlist eth1 scan
iwconfig eth1 ap xx:xx:xx:xx:xx
iwconfig eth1 essid "xxxxxxx"
dhclient eth1 
```

what am i missing, any help would be greatly appreciated! :)

---

### Post by AsburyPark on 2005-08-17
](*,) 
 ](*,) 
 ](*,) 
 ](*,) 
 ](*,) 
 ](*,)

---

### Post by Lambert on 2005-08-17
You may want to repost this under networking. Somebody there browsing may be able to answer this better/faster.

---

### Post by MikeyXX on 2005-08-17
[QUOTE=AsburyPark]I need help connecting to my wireless network.  My card works (iwlist eth1 scan), it shows my network.  I have set my AP and Essid.  I just think I'm missing a step in here.  

```
 iwlist eth1 scan
iwconfig eth1 ap xx:xx:xx:xx:xx
iwconfig eth1 essid "xxxxxxx"
dhclient eth1 
```

what am i missing, any help would be greatly appreciated! :)[/QUOTE]
 Why aren't you using the networking section of KDE/Gnome? You should be able to offer the same confirmation of settings there. Then go into synaptic and do a search for wireless and snag an app that will show you the strength. 

Also, home routers are notorious for being picky on connection, so go unplug it and then pug the power back into your wireless router. That works for me most of the time.

---

