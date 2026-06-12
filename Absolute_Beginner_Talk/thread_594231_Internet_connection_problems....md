---
title: "Internet connection problems..."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Jim2029 on 2007-10-27
i just installed Xubuntu 7.1 on my machine. I found a blog explaining how to get my wifi card working. But I'm woundering about my Nic card. Its a Netgear FA410TX pcmcia card. the only way i can get online is if i have it plugged in and the cat5e cable plugged in BEFORE i boot the laptop on. Y is this? Its set to DHCP... don't make since to me.

---

### Post by auxilum on 2007-10-28
Do you have a  firewall running?  If so, do you allow the DHCP protocol so your machine can obtain an IP address from your router or modem?

Also, try going into System > Administration > Network, and uncheck and check again the box beside your network connection to make Ubuntu look again for your connection.

---

