---
title: "USB Ethernet Adapter won't recognize"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by piperdown10 on 2008-04-03
I have a SMC USB ethernet adapter that when I plug it into my desktop it shows that there's an IP address but won't connect to the internet. I'd like to be able to get on with my desktop (I'm online with my notebook right now). Any suggestions?

---

### Post by nathansoz on 2008-04-03
can you give us the output of

```
lspci | grep Ethernet
```

---

### Post by piperdown10 on 2008-04-03
Can't copy/paste it as it's on seperate computers but this is what I've got:

02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

---

### Post by piperdown10 on 2008-04-03
Don't know if this helps but I used to have an ethernet adapter until it got zapped by lightning and then my ISP gave me an adapter. Could that be the one that it's picking up in the lspci?

---

### Post by nathansoz on 2008-04-05
If it got "zapped" I want to say no. Just to check why dont you try:
```
ifconfig eth0 up
```

---

### Post by piperdown10 on 2008-04-06
So I tried typing:

ifconfig eth0 up

And I got an error message:

SIOCSIFFLAGS: Permission denied

So then I tried it as root and when I typed it, it paused for half a second and then sent me back to the command prompt. I pulled up FF and still no internet.

---

### Post by piperdown10 on 2008-04-20
So I've decided to purchase a new ethernet card. I think that would be easiest and I won't have to worry about taking up a usb slot. So my question now is: what's a decent ethernet card for cheap? I've seen several online that range from $10 - $20. Is that the going price now? What should I look for in features? Will I have to download any drivers or will Ubuntu support plug and play?

---

### Post by piperdown10 on 2008-05-08
Okay, so I've finally purchased a Linksys PCI Etherfast card. I got it home and plugged it in (to a new slot to be sure) and I get nothing. I checked and the drivers are not installed and plug and play did not recognize. How do I get this up and running?

---

