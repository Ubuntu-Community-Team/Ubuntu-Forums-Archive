---
title: "WEP questions"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by philefluxx on 2005-12-20
Ok so Ive made the jump from Fedora Core to Ubuntu and I think I like Ub better. But Im having trouble connecting to my wireless network. The wireless card seems to be working fine and it allows me to configure and activate the connection. It also does see the network and allows me to set my WEP, but we have changed the index on our network. I cannot find where I change the index on the wireless connection settings. Can you change it in Ubuntu. Ive been looking all over google.com/linux and I havent been able to find any information. Please help. Thanks.:confused:

---

### Post by audax321 on 2005-12-20
The easiest way that I've found to do it is to just edit the /etc/network/interfaces file. There is a space in there for wireless-essid and wireless-key.

Then just do:

sudo ifdown (name of connection, like eth0 eth1 or whatever it is)

then

sudo ifup (name of connection)

and it should connect.

---

### Post by Gandalf on 2005-12-20
I suggest to use also wifi-radar
sudo apt-get install wifi-radar

or if you like a gnome applet that you might want [gtkwifi](http://gtkwifi.sourceforge.net/) they have an ubuntu deb package

---

### Post by philefluxx on 2005-12-21
Thanks for the input Ill give that a shot.

---

