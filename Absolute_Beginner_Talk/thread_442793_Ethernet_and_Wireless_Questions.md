---
title: "Ethernet and Wireless Questions"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Platinum J on 2007-05-13
Hello Good People, 

I have a couple of questions. I have an Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter and it works fine on Feisty. The only thing is I have to run ifdown eth1 and if dhclient eth1 in the terminal everytime I start up in order for it to work. I was wondering if there was way to automate this or a way to avoid doing this. Additionally, I have many issues with the wired connection ethernet card and I don't use it at all, so I just do want to disable it permanently. I know I can run ifdown, but I would like to know if there is a way to do this permanently. Well, that covers it. 

Thanks much, 

The Platinum One

---

### Post by Bachstelze on 2007-05-13
Please paste your /etc/network/interfaces file.

For disabling the wired NIC, you can just blacklist it's driver. What kind of card is it ?

---

