---
title: "Finding HP PSC 1317 printer on wireless printserver F1UP0002"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-20
I have:

Belkin router with 4 wired connections & wireless running DHCP

PC with Kubuntu 7.10 on 192.168.1.4, wired to router

HP PSC1317 USB printer connected to a Belkin F1UP0002 wireless printserver which is in turn wirelessly connected to the router

What direction should I be researching in, in order to connect Kubuntu to the printer?

I'm so lost at the moment, I don't even know what IP address the printserver has got.

any general pointers much appreciated

[edit] found the printserver on 192.168.1.2. Guessed it, pinged it, looked at it with arp whereupon that ip reported the mac address of the printserver. A google search suggested connecting to it using LPT :confused:

[edit] my god it works (set it up via CUPS):

```

Description: Belkin F1UP0002
Location: 192.168.1.2
Printer Driver: HP PSC 1310 Foomatic/hpijs (recommended)
Printer State: idle, accepting jobs, published. 
Device URI: socket://192.168.1.2

```

It's be nice to try and connect to it via a hostname of some sort though in case it loses it's DHCP-assigned IP address at some point - ?

[edit] ok, got over that hurdle by realising the printserver is on a static IP 192.168.1.2, the router starts doing DHCP from 192.168.1.3 upwards.

This thing is a pig at the best of times under Windows & Belkin don't seem to provide any Linux support at all, so I'm amazed I've got it to do anything :guitar:

Anybody know if the HP PSC 1317's scanner can be gotten going over this belkin F1UP0002 wireless printserver thing on Kubuntu.. TBH not holding any hopes up for it but if you're reading this & figure it out let us know

(I'm suspecting I need some sort of better, bidirectional firmware for the belkin F1UP0002 printserver device, belkin don't seem to do anything for linux or even, vista)

Tried to run Belkin's Windows XP printserver software under wine but it wasn't having any of it :(

---

