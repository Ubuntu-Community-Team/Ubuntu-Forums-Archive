---
title: "Internet connection- what driver should I be using and how do I install it?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by ezirkara on 2007-12-28
I just installed Ununtu 7.10 on my laptop [sony vaio vgn-nr120e] that came with windows vista. I still have windows vista on the other side of a partition. My internet works fine in Vista, but I can't even detect the presence of wireless networks in Ubuntu. I'm guessing that the wireless card I have [LAN-Express AS IEEE 802.11g PCI-E Adaptor or Marvell Yukon 88E8039 PCI Fast Ethernet Controller (I don't know which is the one I need to connect to the internet)] is not automatically supported by Ubuntu. I've heard that I need to use ndiswrapper or madwifi. How do I obtain and install those and how do I set them up to use my driver from windows to use my wireless card to connect to wireless networks?? This is really confusing to me :confused:and I would REALLY appreciate any help.

---

### Post by spiderbatdad on 2007-12-28
Hi. could you please paste the results of the command ```
sudo lshw -C Network
```
into a post to help diagnose. The command must be entered exactly...case sensitive, and that is a lower case L not a 1.

---

### Post by azelter on 2007-12-28
You do need to use ndiswrapper. Go to your system menu and open synaptic package manager. Search for ndiswrapper. Install that, plus the graphical front end (ndisgtk). For general instructions on using ndiswrapper you can go to their website ([http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)). You can obtain your wireless driver directly from sony ([http://esupport.sony.com/US/perl/swu-list.pl?mdl=VGNNR120E&LOC=3](http://esupport.sony.com/US/perl/swu-list.pl?mdl=VGNNR120E&LOC=3)).

---

### Post by spiderbatdad on 2007-12-28
Hi hope the above post helps, but the Marvell driver on that link is not your wireless driver according to your original post. That is your ethernet driver. Your wireless appears to be supported according to what I have read and you probably just need the package wpa-supplicant...also in synaptic.

---

