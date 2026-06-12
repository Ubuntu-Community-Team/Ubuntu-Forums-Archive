---
title: "Installing Wireless"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Arievilo on 2008-02-25
Good day,

I'm trying to install and configurate my wireless card in my laptop.

This is my Wireless Card
```
reality@reality:/etc/network$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945

```

However when I type iwconfig:

```
reality@reality:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

In network manager I can't find the wireless board to configure, only the eth0 (wired one) and some other modem.

Tried to follow other topics but the ones I've read didn't help me that much, if anyone could guide me would appreciate.

---

### Post by Crooksey on 2008-02-25
```

$ sudo modprobe ipw3945
$ sudo /etc/init.d/ipw3945d start
```

That should load the ipw3945 drivers, now run 

```

$ iwconfig
```

---

