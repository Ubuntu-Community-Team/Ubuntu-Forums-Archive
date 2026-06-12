---
title: "i need help with wireless"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by rob1984 on 2007-08-16
I've recently installed ubuntu fiesty dual boot with winxp. my wireless connection works fine with windows but not in ubuntu.

it will detect nearby wireless networks but not connect.
i have disabled wep - still no luck.
i've also tried turning off roaming mode and configuring manually.

i've never used linux before can anyone help please??

card: 
ralink 2500 mini pci 802.11g

output of lspci:
00:11.0 Network Controller: RaLink RT2500 802.11g Cardbus/Mini-PCI (rev 01)

---

### Post by wolfen69 on 2007-08-16
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

---

### Post by rob1984 on 2007-08-16
still no luck.  i've found a driver on the ralink website but its source and i cant compile it.  i've tried my best but i keep getting error 1 or error 2.  i dont know what this means.

can anyone help??

---

### Post by yogo on 2007-08-16
I would use NDISwrapper to install the .inf driver file and you should be good to go.

That is what i used for  rt61 ralink edimax pci card.

---

### Post by rob1984 on 2007-08-16
cool. ive already downloaded that but im having trouble installing it.  ill keep hacking and let you know how i get on.  cheers.

do you know what the error 1 and 2 are?

---

### Post by fredj on 2007-08-17
If your existing driver detects your networks then you may not need to install the Windows
drivers using ndiswrapper.
One of the problems with the rt2500 seems to be that it doesn't work well with network-manager.
I recently configured a rt2500 card with windows drivers but it still wouldn't connect. I solved the
problem by uninstalling network-manager and network-manager-gnome and then installing wicd
which is available for ubuntu.

---

### Post by rob1984 on 2007-08-17
cheers everybody NDISwrapper worked a treat!

cheers yogo.

---

