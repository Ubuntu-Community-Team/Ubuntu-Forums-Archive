---
title: "Network Manager Gnome"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-12-06
I made a new thread, because -no where- have I found anything to help here.

I "sudo apt-get install network-manager-gnome", now how do I use it?

Where do I open it from? I looked all over the menu, and it's not there. 

Seems odd that something so simple is becomming a frustrating task, amongst my other battles tonight.

Did I just overlook something?

---

### Post by sonny on 2006-12-06
Well it should appear in the tray bar in your panel, go to system>preferences>sessions then go to the startup programs tab and make sure you have the following command: nm-applet --sm-disable if you don't have it then that's the place it should be... add it with the add button. Then logout and then back in... it should appear in the tray bar.

---

### Post by Taigrr on 2006-12-06
It's there. And apearently, it's working on the wired Eth0 connection. But I can't figure out how to make it work on the Wireless eth1 connection. Any secrets?

---

### Post by Patrick-Ruff on 2006-12-06
umm, you should just be able to change it to eth1.

---

### Post by sonny on 2006-12-06
Make sure your /etc/network/interfaces file looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0
```

---

### Post by Taigrr on 2006-12-08
Hm. Well, I get it to work okay. apt-get install network-manager-gnome, and reboot. And it comes up working. I can click it and see the diffrent networks and how strong their signal is. But it seems like when I update, (Or reboot), it changes. The wireless card still works, so it has to still be there. But I can't just choose a wireless from the drop down like I could before.

Is it just an update in the manager? Or is there a config file I need to edit somewhere?

---

