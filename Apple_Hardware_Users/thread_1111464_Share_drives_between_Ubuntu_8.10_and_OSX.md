---
title: "Share drives between Ubuntu 8.10 and OSX"
date: 2009-03-30
forum: Apple Hardware Users
---

### Post by thenaesh on 2009-03-30
So I have two laptops:
One is an HP running Ubuntu 8.10 
The other is a MacBook running OSX Leopard

I want to have two way sharing between the computers as long as they're both on the internet (or at least on the same network). I have installed Netatalk and Avahi on the HP and can access the Ubuntu computer from the mac. 

I have some external HD and a USB hub attached to the Ubuntu computer. I want file sharing such that whenever I attach a USB drive to the USB hub (which is attached to the Ubuntu computer) I would like it to show up on the Mac desktop as if I had plugged it into my MacBook. 

Is it possible to give both computers equal access to external USB drives even if they are only plugged into one computer? I would prefer two way sharing, but if the Ubuntu computer could share with the MacBook that would be good enough. 

Thanks

---

### Post by cyberdork33 on 2009-03-30
> **thenaesh said:**
> So I have two laptops:
One is an HP running Ubuntu 8.10 
The other is a MacBook running OSX Leopard

I want to have two way sharing between the computers as long as they're both on the internet (or at least on the same network). I have installed Netatalk and Avahi on the HP and can access the Ubuntu computer from the mac. 

I have some external HD and a USB hub attached to the Ubuntu computer. I want file sharing such that whenever I attach a USB drive to the USB hub (which is attached to the Ubuntu computer) I would like it to show up on the Mac desktop as if I had plugged it into my MacBook. 

Is it possible to give both computers equal access to external USB drives even if they are only plugged into one computer? I would prefer two way sharing, but if the Ubuntu computer could share with the MacBook that would be good enough. 

Thanks
well, I'd probably use samba instead of netatalk... and you can setup to share all of /media and that should cover anything that automounts on Ubuntu.

---

