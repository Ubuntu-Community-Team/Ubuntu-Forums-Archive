---
title: "Recover Wireless Connection"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Otto-C on 2006-07-21
Need to recover 'Wireless Connection" on Network Settings Menu.
Accidently did a deactivate and the choice 'Wireless Connection' disappeared from the choices menu including Ethernet Connection
and Modem Connection.
tia
Otto-C

---

### Post by dalonso on 2006-07-21
Same here. It seems that NetworkManager daemon is killing my CPU while not finding any wireless network, so it doesn't report any network name to the nm-applet.

Read somewhere that erasing gconf settings is System/Networking/wireless resurrects NetworkManager daemon, but how the hell do you erase them. I remover the drawer "wireless" from ~/.gconf/System/networking and upon reboot it is there again.

Something very odd happening with NetworkManager!!!

---

### Post by Otto-C on 2006-07-22
From reading other sites if you do

from root

sudo modprobe ndiswrapper will cause

the wireless option to return to the

network wireless assistant menu.

Otto-C

---

