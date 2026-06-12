---
title: "HOW TO: start gnome"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2006-05-15
I installed Ubuntu 5.10 from the installation CD. I chose the default install (not 'server'). During the installation one problem occurred: it failed to connect to the ubuntu server because the network settings could not be recognized. I configured the network settings manually. My PC has a wireless connection to a router which dynamically assigns IPs to all clients. I entered an IP for my Ubuntu machine and the gateway address as well.

When Ubuntu starts, I come to a command line login and then come to the command line bash shell.

From here, how do I get to a graphical user interface (gnome)?

I have tried startx, however, it takes me to an empty screen with some icons. When I click somewhere, the icons disappear and all that is left is an empty screen that says (nautilus).

I am absolutely new to all this and appreciate any kind of help!

Thanks in advance, Anders

---

### Post by Sef on 2006-05-15
Sounds like GNOME didn't install correctly.  So try this from the command line:

sudo apt-get update

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

---

### Post by ahlandberg on 2006-05-15
Eureka! I simply re-installed Ubuntu and now it worked ... no idea what went wrong last time!!

Thanks anyways!!

---

