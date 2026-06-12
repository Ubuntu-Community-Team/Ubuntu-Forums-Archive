---
title: "LAMP Installation problem, please help..."
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by stokerfed on 2006-09-19
I'm trying to install the Ubuntu LAMP Server, but I keep getting this error.

I'm not sure how to setup the network manually, but if someone with knowledge could help me that would be great.

[ATTACH]15984[/ATTACH]

Do you think I might be getting this because its on a virtual machine?

---

### Post by mssever on 2006-09-19
I know nothing about running in a virtual machine, but if you use a static IP (you probably should if you're running a server), you can configure it directly by editing /etc/etwork/interfaces.

For example, the interfaces file on my server includes the following:
```
auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
```

Be sure to restart networking in order to apply any changes:
```
sudo /etc/init.d/networking restart
```

---

### Post by stokerfed on 2006-09-19
thanks so much for the reply, the problem ended up being the way I had my VM setup. I had to choose the ethernet to be custom: VM(8)NAT.

Now it connected no problem.

---

