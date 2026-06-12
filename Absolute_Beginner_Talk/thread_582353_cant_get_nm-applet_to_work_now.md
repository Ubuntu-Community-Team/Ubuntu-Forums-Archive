---
title: "cant get nm-applet to work now"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-10-19
I was screwing around with my network settings through sys>admin>network
I assigned a static for a class, since then my nm-applet shows no wireless

In order for me to get my wireless working now i have to 
pull-up network settings
disable/enable wireless connection
then 
sudo /etc/init.d/networking restart

this works but once again the nm-applet stays dead the whole time

in my /etc/network/interfaces i have

auto lo
iface lo inet loopback

Obviously, each time i disable/enable the settings through my network settings it adds an entry into my /etc/network/interfaces file


Can anyone get my nm-applet back to working???

---

### Post by charles.g.moore on 2007-10-19
I just want my system's wireless back...

---

