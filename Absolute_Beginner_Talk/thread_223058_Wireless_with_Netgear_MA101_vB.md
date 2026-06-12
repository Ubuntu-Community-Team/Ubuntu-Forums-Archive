---
title: "Wireless with Netgear MA101 vB"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by mohitii on 2006-07-25
I've downloaded the atmelwlandriver and extracted it, which is recommended for the MA101.  I also have ndiswrapper installed.  What do I do now to get the wireless working?  My comp has access to the internet through ethernet, but wireless would be much appreciated.  (the router is a netgear g but I don't remember the model number.  I can go look if necessary.)

---

### Post by H.E. Pennypacker on 2006-07-25
The router information is not relevant.  First, go to the ndiswrapper wiki to see if ndiswrapper supports it.  If it does, install the driver using ndiswrapper, or use gtk-wifi to do it.  Honestly, I would recommend using GTK-Wifi, which is a GUI version of ndiswrapper.  While you're on the ethernet connection, install GTK-Wifi from Synaptic.

Once you're done installing the driver, switch over to Network Connections, and set up your internet connection.  Search the Ubuntu Wiki on how to use Network Connections.

---

