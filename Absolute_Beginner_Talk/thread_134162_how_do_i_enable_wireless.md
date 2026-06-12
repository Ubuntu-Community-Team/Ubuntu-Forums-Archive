---
title: "how do i enable wireless?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-02-21
I have installed the driver for my hardware, both are present. I dont know what my connection settings are e.g.

IP address
Subnet mask
Gateway Address 

I dont think I have a WEP key and whats the connection type?
Thanks in advance for any help :-D

---

### Post by KingOfNowhere on 2006-02-21
there is an easier way to use your wireless card

install this:
```
sudo apt-get install networkmanager
```

then once it is installed:
```
nm-applet
```

This will start the NetworkManager applet that sits on your panel. NetworkManger will completely handle your wireless configuration for you and select the best internet connection to use.

---

