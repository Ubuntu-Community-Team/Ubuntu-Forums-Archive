---
title: "Recognizing a Ubuntu Machine over a LAN via Hostname"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by climbjm on 2007-09-15
I have a tiny LAN of my own.

**My Setup:**
Comcast Internet > Modem > Router (wired).
Router > One Wireless WPA2 Access Point > Laptops
Router > Ubuntu File Server

If I type in my wifes laptops host name, I can access her shared folders no problem.
If I type in my Ubuntu computers **host name**, I **cannot** access the SMB file share.
If I type in my Ubuntu computers **ip address**, I **can** access the SMB file share.

Is there a way to allow my laptops find the Ubuntu Server via host name?  That way I dont have to have my wife type in the IP address to upload her photos.  Plus the router is set up for DHCP (not static) and if the address changes, it makes things more difficult.

My Router does Not support turning off DHCP (its an old router).  It does not allow me to assign IP' to MAC addresses (reservations).

Ideas?

---

### Post by mocoloco on 2007-09-16
I'm curious about this also.  I was told that it's because Windows systems use [WINS]("http://en.wikipedia.org/wiki/Windows_Internet_Name_Service") to know hostnames, and that's a distributed service where all computers manage and store all hostnames, whereas Linux would use [DNS]("http://en.wikipedia.org/wiki/Domain_name_system") which expects you to have a DNS server to be able to use hostnames.  I don't know how correct that is, I need to learn more about networking.
Gurus in the know, please enlighten us.

---

### Post by Koybe on 2007-09-16
If you're using samba, you can use the nmbd daemon to resolve names using WINS. The best is DNS because it's not broadcasting everywhere on your network but it needs more configurations.

So you can try editing your /etc/samba/smb.conf on your samba server, then enable wins support ```
wins suport = yes
``` It's at the beginning of the file. If you have samba clients, you can tell who is your WINS server by editing one more time your samba configuration adn adding ```
wins server = 192.168.1.1
``` where the ip is the one of your server.

You can also tune this a little bit using the 'name resolve order' parameter.

You can find detailed informations [here]("http://www.oreilly.com/catalog/samba/chapter/book/ch07_03.html")

---

