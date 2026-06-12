---
title: "LAMP Configure network manually...."
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by stokerfed on 2006-09-19
Trying to install Ubuntu LAMP is not working smoothly on my virtual machine. Does anyone know how to configure the network manually with my IP settings?

---

### Post by mssever on 2006-09-19
I'm not positive I understand you since you've provided hardly any information, but I'll give it a shot.

If you want a static IP, you can configure it in /etc/network/interfaces.

For example, I have the following:
```
auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1

```There's probably a GUI way to configure this, but I wouldn't know about it.

To apply any changes, type
```
sudo /etc/init.d/networking restart
```

---

