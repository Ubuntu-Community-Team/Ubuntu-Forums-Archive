---
title: "network card works, but not for network-manager?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-19
is it possible that i can connect to a wireless network, but that the network-manager can't pick up the available networks with it? that seems like exactly what is happening. i am connected and great, but when i try to switch, network-manager doesn't come through for me. i right click it in the tray and it says enable networking, but nothing wireless. networking is enabled but never active since i'm only wireless..any ideas?

---

### Post by shanepardue on 2006-09-19
seems like a simply question, but i am not sure of the answer. help is greatly appreciated.

---

### Post by happy-and-lost on 2006-09-19
```
sudo apt-get install wifi-radar
```

:D

---

### Post by shanepardue on 2006-09-19
> **happy-and-lost said:**
> ```
sudo apt-get install wifi-radar
```

:D
ok, that's cool..but is there something like that you can access from your tray like airport with mac?

---

### Post by orb9220 on 2006-09-19
for nm-applet to start working I had to edit 

gksudo gedit /etc/network/interfaces   and comment out all the lines but lo

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#auto ath0

Then all the ssidd's started to show up.

---

### Post by shanepardue on 2006-09-20
is that applet supposed to look like this attached picture? if so, it's not working for me even after i comment out what you said.

[IMG]http://img.photobucket.com/albums/v330/shanepardue/wireless-at-tealuxe.png[/IMG]

---

### Post by shanepardue on 2006-09-21
this is what my networkmanager looks like and it only shows enable networking when i right click it. pls help!

[IMG]http://img.photobucket.com/albums/v330/shanepardue/Screenshot-2.png[/IMG]

---

### Post by shanepardue on 2006-09-21
anybody? it's really annoying trying to switch networks as i have it set up now. thanks!

---

### Post by devinkray on 2006-10-05
I am having the same trouble it seems that the program doesn't reconize my wireless card, which im using ndiswrapper to start,

And yes I've looked through the wiki's but nothing seems to help.

---

