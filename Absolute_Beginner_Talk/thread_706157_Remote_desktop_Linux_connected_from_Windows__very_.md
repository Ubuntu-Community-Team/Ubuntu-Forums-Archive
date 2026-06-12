---
title: "Remote desktop Linux connected from Windows : very slow"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by idy on 2008-02-24
Hello,

I am connecting from Windows to Ubuntu via remote desktop.
On my Windows machine, I am using putty and TightVNC (SSH tunnel connection).

When I had the Ubuntu machine on my LAN, it went very fast. Now the Ubuntu machine is in another location, but it takes ages for the screen to refresh on my side.

Any ideas on how I can configure options in TightVNC or somewhere else to increase the speed (by reducing quality, etc.) ?

FYI, I did not modify the default options of the latest Windows version of TightVNC.

Thx a lot !

---

### Post by skymera on 2008-02-24
Does the ubuntu box have any desktop effects enabled?

---

### Post by (((X))) on 2008-02-24
I use ULTRAVNC(client),realvnc is an alternative.. not sure it´s better..

---

### Post by idy on 2008-02-24
@skymera : indeed, advanced FX enabled. I will put no effects next time I connect to it. Thx for implying this.
@X : not sure either that is is better, but thx for suggesting !!

---

### Post by idy on 2008-02-24
Here are the options of Tight VNC on the following image :
[IMG]http://idy.free.fr/ubuntu/vnc%20options.JPG[/IMG]

I checked 8-bit color but it did not seem to change a lot when I did that earlier today.
Still have to remove the desktop settings.

Any ideas on other options to check / uncheck to improve the speed on my (client) side ?

Thx

---

### Post by (((X))) on 2008-02-24
I don´t know how it goes through internet, only used to conect to computers on the LAN network, LAN is much faster than Internet, So I can´t give you advice that will be usefull in your case.

From my experience with bittorrent, torrents load faster when you forward special ports ,so I would recomend you to forward some ports.


Assuming you have control of you server..

---

