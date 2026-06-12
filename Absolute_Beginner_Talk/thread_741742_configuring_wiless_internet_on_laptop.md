---
title: "configuring wiless internet on laptop"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by ddalton on 2008-04-01
Hi,

I have a ubuntu laptop here. Its running version 7.10 (gutsy).
I also have a wiless internet card. I believe it is a sisco 340/350... Ok ubuntu seems to recognise when I plug it in. So how do I connect to a network?
I think its recognised and eth1.

So what exactly needs to be done to connect to a wpa network and an unsecure network?
I prefer to use the command line since I'm blind, but if I must use the gui I can use gnome...

Thanks for any help.

Daniel

---

### Post by _aXXe_ on 2008-04-01
A bit more information would be helpful.
Do you connect to a wireless router in your home, business or web cafe'?
If you connect at home, your router should have the information you need in conjunction with the software you installed for the wireless card on your laptop. This would be either the LINUX drivers for your card supplied by the manufacturer or the driver used by Ubuntu.

Access to the router would be along the lines of whatever the router default is. D-link uses 198.162.0.1 and Cisco uses 192.168.1.1 in you web browser. Generally the id is admin and the password is blank.
Otherwise you'll need the information at the site you use to gain access to their network.

Your wireless card should should offer you a list of available networks in range when it's active. Both secure and unsecured should be listed.

Unsecured should allow you to connect once you choose one.
Maximum range is limited to about 300 feet for 802.11b and 802.11g. 802.11n is about 1100 feet.

---

### Post by ugm6hr on 2008-04-01
This should point you in the right direction: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

This will tell you whether the card has actually been recognised
```
lshw -C network
```

---

### Post by ddalton on 2008-04-01
> **_aXXe_ said:**
> A bit more information would be helpful.
Do you connect to a wireless router in your home, business or web cafe'?Hi,
If you connect at home, your router should have the information you need in conjunction with the software you installed for the wireless card on your laptop. This would be either the LINUX drivers for your card supplied by the manufacturer or the driver used by Ubuntu.
Ok thanks for the reply!
Access to the router would be along the lines of whatever the router default is. D-link uses 198.162.0.1 and Cisco uses 192.168.1.1 in you web browser. Generally the id is admin and the password is blank.
Otherwise you'll need the information at the site you use to gain access to their network.I know all the info for it since its my home router, however, someitmes I will want to connect in public libraries and hotels.
So with all the information how do I connect?
Your wireless card should should offer you a list of available networks in range when it's active. Both secure and unsecured should be listed.I believe my card is being recognised as eth1...

Unsecured should allow you to connect once you choose one.Oh and how do I scan for networks?
Maximum range is limited to about 300 feet for 802.11b and 802.11g. 802.11n is about 1100 feet.Its secured with wpa...

Thanks for your help,

Daniel.

---

