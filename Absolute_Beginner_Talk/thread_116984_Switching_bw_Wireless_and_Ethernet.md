---
title: "Switching b/w Wireless and Ethernet"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by hwliang on 2006-01-13
Hello all,

I am relatively new to the Linux world (my first attempt was installing Fedora last summer), and I just installed Ubuntu maybe two weeks ago. Let me tell you, Ubuntu has made it one very enjoyable experience for this newbie, even if I do tend to break things often with all of my tinkering (there are just so many tempting How To's in this forum!). Anyway, on to my question.

I am often switching between ethernet and wireless (installed through ndiswrapper). Currently, I've found that the only way to switch between the two is to go to System -> Administration -> Networking and manually deactivate one and activate the other. Is there a way for Ubuntu to automatically detect when I switch from one to the other (like in WinXP)? If not, is there a more convenient way for me to switch between the two without having to do all of the above (i.e. a connection management app, a gdesklet, etc)? I would appreciate any ideas. Thanks!

---

### Post by JimmyJazz on 2006-01-14
well each network adapter has a name (like eth0 or eth1) the first thing is to figure out what those names are in your setup (probally the ones I just listed)
then you can type in terminal...

sudo ifup eth0

this will bring up your eth0 device but you need to take the other one down and its just as easy

sudo ifdown eth1

that command will take down device eth1

this said you can make a bash script to switch between the two

example:

#/bin/bash

sudo ifdown eth1
sudo ifup eth0


save that file as "switch_card" and change its permission to 755

---

### Post by nalmeth on 2006-01-14
if you're using gnome you can add a network monitor to your toolbar, and I believe you could change from wlan0 to eth0 there. I know little about all this wireless noise, so thats all I can suggest.

---

