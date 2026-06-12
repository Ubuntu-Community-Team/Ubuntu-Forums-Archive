---
title: "Can't get my wireless to work - odd situation"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-09-23
Okay, I'm able to connect to my wireless network at home on both WEP and WPA secuirty just fine. However, I can't login to the network at school for some reason.

When I switch over to windows I can log onto it just fine, but for some reason I can't get the network manager in ubuntu to connect me to the freaking thing.

Here's what my school's site has to say about wireless access
> 64 bit cards: WILL NOT FUNCTION ON THE UC WIRELESS NETWORK.
128 bit cards: Set the transmit key to be Key 1.


Depending on the manufacture and version of software, it will ask that the keys be entered in either ASCII or Hex. Choose the appropriate one or else it will not communicate with the access point.

UC SSID is NoWireUC. (case sensitive and required)

Now, when I use the network manager, I use the 64/128 bit WEP encryption option and put in the password they give to everyone, but I can never get it to connect to their network on ubuntu.  I don't know if I have the transmit key set to 1 cause I don't know how to check or do it.

---

### Post by julian67 on 2007-09-24
There's a bug open for exactly this: [https://bugs.launchpad.net/baz/+bug/114605]("https://bugs.launchpad.net/baz/+bug/114605")

Meanwhile you *can* connect to your school network but you'll have to do it manually. There is an example you can follow in the above bug report.

---

### Post by CryptiniteDemon on 2007-09-27
Okay here's the weird thing.  Network manager will automatically find and configure any connection at my school everywhere except for one place.  At this one place the network will never connect even though the signal is pretty good. I was able to connect at several other locations, but this is the only one I can't get ubuntu to connect to.  

However, it does connect on windows.

---

