---
title: "Wireless card recognition"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-03-20
Having finally managed to install Xubuntu on an older laptop I am able to access the internet via a ethernet cable from my Belkin modem router. but the belkin wireless card on the laptop was not automatically recognised during installation.  How can I set this up please?

---

### Post by Kobalt on 2007-03-20
What is the exact model of your Belkin card ?

---

### Post by a.v.l on 2007-03-20
> **Kobalt said:**
> What is the exact model of your Belkin card ?

Thanks for your post, unfortunatly I'm at work and don't have that information, but I will post the model number this evening.  The modem/router itself is a Belkin 54Mbps ADSL Modem with wireless -G router  model F5D7632-4 if that help at all.

This is to confirm the Belkin wireless card I'm trying to install on my laptop.  It is a "Belkin G Notebook Network Card" model number F5D7010. All help welcomed.

---

### Post by a.v.l on 2007-03-20
> **a.v.l said:**
> Thanks for your post, unfortunatly I'm at work and don't have that information, but I will post the model number this evening.  The modem/router itself is a Belkin 54Mbps ADSL Modem with wireless -G router  model F5D7632-4 if that help at all.

This is to confirm the Belkin wireless card I'm trying to install on my laptop.  It is a "Belkin G Notebook Network Card" model number F5D7010. All help welcomed.

Laptop is a Samsung V25.

---

### Post by Kobalt on 2007-03-20
The belkin F5D7010 seems to be built on a Ralink RT2500 chipset that is natively supported by Ubuntu since 6.10. You shouldn't need to install any driver then.
Here is some doc on configuring your wireless connection : 
[http://doc.gwos.org/index.php/WirelessStarterGuide](http://doc.gwos.org/index.php/WirelessStarterGuide)

I suggest you install Network-manager in order to manage your wifi connection easily : 
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by a.v.l on 2007-03-20
> **Kobalt said:**
> The belkin F5D7010 seems to be built on a Ralink RT2500 chipset that is natively supported by Ubuntu since 6.10. You shouldn't need to install any driver then.
Here is some doc on configuring your wireless connection : 
[http://doc.gwos.org/index.php/WirelessStarterGuide](http://doc.gwos.org/index.php/WirelessStarterGuide)

I suggest you install Network-manager in order to manage your wifi connection easily : 
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Thanks, but unfortunatly my laptop specifcations will not allow me to install unbuntu.  The best I've managed is to install Xubuntu 6.6

---

