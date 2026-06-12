---
title: "why torrent works in windows and not in linux"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-07-06
Hi
Thank you for reading my post
I have a big problem with my Linux and that is its problem with torrent and mule.
Utorrent works fine in my windows installation and Azureus or ktorrent does not works in Ubuntu 7.04 Kdesktop.

here is some information that may be useful to resolve my problem.

1- I uninstalled firestarter.
2- here is out put for sudo iptables -L

```


sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```


what else can restrict my torrent application to work fine?

thanks

---

### Post by splintercellguy on 2007-07-06
What exactly is the problem?

---

### Post by blithen on 2007-07-06
Are you dual booting? 'Cause you can always install wine and run uTorrent.

---

### Post by legolas_w on 2007-07-06
Hi
Thank you for reply.
problem is that i can not download anything from torrent when i am using linux.
Azureus and Ktorrent does not download anything but when i am in windows uTorrent download files in a good speed.

---

### Post by eternalsword on 2007-07-07
try deluge.  [http://deluge-torrent.org](http://deluge-torrent.org)

---

### Post by BoneSaw on 2007-07-07
im sure you know enough about torrents to have checked this, but are you sure you have the right ports forwarded. ktorrent and azureus both have configurable listen ports.

---

### Post by misfitpierce on 2007-07-07
Utorrent is not a great idea on any system... It was purchased by RIAA or something... So id stick with azureus or transmission....

 Transmission can be found off [http://getdeb.net](http://getdeb.net)  works great on ubuntu

---

### Post by ugm6hr on 2007-07-07
Why did you uninstall Firestarter?  It makes opening iptables ports much easier.

And, as mentioned, ensure the correct ports are opened.  I'd recommend changing the ports (in KTorrent) to the same ones that utorrent uses in Windows, so the ports should already be forwarded from your router.

Then start a torrent, open Firstarter, and it will "event" - just open the "event" port (which should be the same as the defined port).

EDIT: Forgot to mention - in KTorrent, go to Configure / Plugins and load the UPnP plugin.  It then behaves like utorrent.

---

### Post by deepclutch on 2007-07-07
get a port set on Azureus.go to Azureus tools menu and NAT Firewall test. enter some random port like 28754 and try ping and if successfull;apply.now it is a good idea to have a small firewall script set for ur ubuntu ,u can try redhat "lokkit"(tui)-with Lokkit,let the aforementioned port be open.there is gui called gnome-lokkit too.

---

