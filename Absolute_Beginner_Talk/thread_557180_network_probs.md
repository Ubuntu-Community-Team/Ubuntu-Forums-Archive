---
title: "network probs"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by ne0 on 2007-09-22
Hi there people.

I'm very interrested in this Ubuntu but have come across a problem. I cannot install my LAN card on Ubuntu... Any suggestions?

my LAN card is "**Realtek RTL8139 Family PCI Fast Ethernet NIC**". It is detected as pci hardware but not recognised as ethernet card n needs to be installed........

**plz give directions....**

THANX

---

### Post by CaptainInsaneO on 2007-09-22
Do this:

```
sudo gedit /boot/grub/menu.lst
```

and add this line at the end of your boot kernel:

```
pci=noacpi
```

Save and reboot. Should be fixed.

---

