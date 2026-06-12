---
title: "DSL issues"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Radiobuzz on 2008-02-03
Hi all!

First of all, I'm an absolute begginer so feel free to treat me like a two-year old :). I've just installed Ubuntu (7.04, upgrading as we speak) and I find it completely adorable. I've tried to use *nix in past times but to no avail, so I find very conforting that Ubuntu is so simple.

I'm just having a small problem, which in fact is not the first time it happens  (it happened also with every other Linux dist I've tried so far). I've configured my DSL PPPOE connection using the terminal and it works like a charm, but the problem is that everytime I reboot the system and log in again, I'm not connected. For instance, I click on the network configuration icon next to the clock and press the option to connect to the dsl-provider, but nothing happens; I don't get any kind of message and I can't surf the web. The same happens when I try to open the connection using the terminal, and also if I try to configure the connection (using pppoeconf) again, it says that it can't find any DSL adapter on the ethernet interface. 

What I did last time (and luckly it worked) was to disconnect my modem, reconnect it and run pppoeconf. As soon as the upgrade is done installing I'll reboot, but probably I won't be able to connect because, as I said, it's not the first time this happens.

Hope you can help me!

---

### Post by dcstar on 2008-02-04
> **Radiobuzz said:**
> Hi all!

First of all, I'm an absolute begginer so feel free to treat me like a two-year old :). I've just installed Ubuntu (7.04, upgrading as we speak) and I find it completely adorable. I've tried to use *nix in past times but to no avail, so I find very conforting that Ubuntu is so simple.

I'm just having a small problem, which in fact is not the first time it happens  (it happened also with every other Linux dist I've tried so far). I've configured my DSL PPPOE connection using the terminal and it works like a charm, but the problem is that everytime I reboot the system and log in again, I'm not connected. For instance, I click on the network configuration icon next to the clock and press the option to connect to the dsl-provider, but nothing happens; I don't get any kind of message and I can't surf the web. The same happens when I try to open the connection using the terminal, and also if I try to configure the connection (using pppoeconf) again, it says that it can't find any DSL adapter on the ethernet interface. 

What I did last time (and luckly it worked) was to disconnect my modem, reconnect it and run pppoeconf. As soon as the upgrade is done installing I'll reboot, but probably I won't be able to connect because, as I said, it's not the first time this happens.

Hope you can help me!

If your router/modem has the capabilities of doing the PPPoE login itself, then you should set it up to do it and just let Ubuntu use the connection via DHCP - it makes things a lot simpler (and more reliable).

---

### Post by Radiobuzz on 2008-02-04
Hi there,

Thanks, but I've solved the problem using a guide I found somewhere. I had to rearrage the order of a couple of lines in the configuration file and now it works perfect!

Thanks anyway.

---

### Post by coldfeet on 2008-02-04
Could you share this guide?  I'm trying to find anything that will help me with the problem I am having with getting connected.

---

### Post by john3347 on 2008-02-04
Please share the guide you speak of.  I am having the exact same problem.  If I close Ubuntu, I have to unplug the computer for a few minutes before the computer will connect to the DSL modem again.   Please!  Thank toy,  John

---

### Post by john3347 on 2008-02-04
Was trying to say "thank you", not "thank toy".   Got excited there and could not type.

---

### Post by Radiobuzz on 2008-02-04
Sorry I couldn't answer before. All you have to do is edit /etc/network/interfaces to put the line that says something like "line mantained by pppoeconf" *before* the line "auto adsl-provider". Something like this:

# added by pppoeconf
auto eth0
iface eth0 inet manual
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

That worked for me, I hope it works for you too.

---

