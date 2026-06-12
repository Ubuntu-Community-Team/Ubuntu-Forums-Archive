---
title: "manual network config in terminal"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-06-01
Hi,
I'm reinstalling my dapper xubuntu with wireless USB.  I know that if I do a server install and then use an ethernet connection to install Xubuntu desktop, my wireless usb works fine, after configuring it using the network settings gui.
What I want to know, just for perversity's sake ;-) is:
Can I manually config the usb wirelss from the terminal after doing just a server install, I don't think I need to install any drivers, just do the equivalent of set the config options from the gui and then activate the device.

otherwise Ihave to unplug the machine, drag it from one room to another, move loads of clobber out off the way, and plug in the ethernet :-( and I'm lazy (or inefficient, or curious!)

---

### Post by hw-tph on 2006-06-01
Network devices are configured using the /etc/network/interfaces file. Good starting points are reading interfaces(5), ifup(8) and iwconfig(8). These are man pages so you type **man 5 interfaces** (and so on) to read them.

If you search this forum you will find lots of examples, and the [Wireless Troubleshooting Guide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide) from the wiki may prove useful as well.

Håkan

---

### Post by damianubuntu on 2006-06-01
cheers, I'll get reading......

---

