---
title: "Setting up Ethernet"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by godsfshrmn on 2007-09-29
Hello,
I am totally new to Ubuntu. I installed the server version, which has only the command-line. I have been running a linux VPS and have some limited knowledge about commands. I am trying to setup my ethernet. I have looked through the forums and the faq, but everything I have tried has yielded no results. I'm really out of ideas of what to try here. Anyone know?

Thanks,
Andrew

---

### Post by MobiusNZ on 2007-09-29
Hi Andrew,

Check out some of these links:
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/")
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking")

---

### Post by dcstar on 2007-09-29
> **godsfshrmn said:**
> Hello,
I am totally new to Ubuntu. I installed the server version, which has only the command-line. I have been running a linux VPS and have some limited knowledge about commands. I am trying to setup my ethernet. I have looked through the forums and the faq, but everything I have tried has yielded no results. I'm really out of ideas of what to try here. Anyone know?

Thanks,
Andrew

Your /etc/network/interfaces file contains all the setup info, here is the contents of mine as an example:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

This will allow you to edit this file:

```
sudo nano /etc/network/interfaces
```

If you want to make your life a lot easier, you can install all of the X desktop tools on your server by installing the **ubuntu-desktop** meta-package.

---

### Post by godsfshrmn on 2007-09-29
Hm I edited the config file successfully, but now when i do an ifconfig, i do not see the eth0. Also, when I restart networking, it tells me eth0:no such device.

---

### Post by cmnorton on 2007-09-29
From the Applications Places System Menu Bar:

System->Administrastion->Networking

When prompted, use the password of the administrator who installed the system.

Configure either wireless, modem, or ethernet, whichever is the network interface you want to use.

---

### Post by godsfshrmn on 2007-09-29
I am trying to stick with the command line only because it will be used as a server, so I don't have the gui.

---

### Post by MobiusNZ on 2007-09-29
Was the network card detected on setup? Can you post the output of the command ```
lspci | grep net
```
If nothing is output, try looking through the full output of lspci (just run lspci) for the network card, and post it.

---

### Post by handydan918 on 2007-09-29
> **godsfshrmn said:**
> I am trying to stick with the command line only because it will be used as a server, so I don't have the gui.

Ya know, jsut because the system has a gui doesn't mean it has to be running all the time. Why not install it and set the default runlevel to 3?

---

