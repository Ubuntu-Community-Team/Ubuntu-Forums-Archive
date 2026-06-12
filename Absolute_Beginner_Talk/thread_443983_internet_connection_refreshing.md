---
title: "internet connection refreshing"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-05-14
Hi,
If I plug-in my internet cable (Ethernet cable) after I turn on my ubuntu machine, it does not recognize the connection. I have to restart my machine after the cable is plugged in. I use edgy.

then I have two questions:

1. is this normal?
2. is there any other way to get the connection recognized other than restarting. (any terminal comment or menu comment is ok)


Thanks in advance...

---

### Post by lloyd_b on 2007-05-14
1.  I'm afraid it is *normal* - the issue is that DHCP (the protocol that automatically sets your IP address and other network parameters) only runs at startup (or when an interface is "brought up").  The simple act of connecting a network cable isn't enough to trigger this process to run.

2. In a terminal window:
```
sudo /etc/init.d/networking restart
```
should do the trick. 

There's probably a way to do this via the GUI as well, but I'm an old command-line junkie, so I have no clue as to what it would be.

Lloyd B.

---

### Post by neodarksaver on 2007-05-14
1. I don't think it's normal.
2. try updating the driver for ur network card. (i don't know the exact procedure or command, someone else please help)

---

