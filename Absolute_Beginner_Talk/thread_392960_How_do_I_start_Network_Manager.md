---
title: "How do I start Network Manager"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by trevoore on 2007-03-25
Hi!

Here's a stupid question: How do I start Network Manager?

I've downloaded and installed the packages for Network Manager and Network Manager Gnome and all the dependencies they asked for.

Then I tried just looking in the file system for the Network Manager application and double-clicking on it. With the help of the package install information I found the following possibilities:

usr/bin/nm
usr/bin/nm-applet
usr/bin/nm-vpn-properties
usr/bin/nm-blookup
usr/share/gnome/autostart/nm-applet.desktop

Nothing happens except with nm-vpn-properties, but that doesn't get me anywhere.
I've tried using the terminal and Alt-F2, same thing. Only with Alt-F2 and nm-applet.desktop he automatically uses gedit. That seems to be a config file then.

I'm using Ubuntu 6.10. Desktop.

My real problem is that I can't get my wireless connection to work, but first things first.
Till there's a solution in sight, it's back to Microsoft Windows.

Cheers,
t

---

### Post by Kobalt on 2007-03-25
Using Alt+F2 *nm-applet* simply should do the trick.

---

### Post by RetepNamenots on 2007-03-25
I tried installing network-manager, same problem (nothing appears in any of the menus or anything).

I think that the built-in Networking options are adequate, and you can enter the access point info, wep etc by using:

> sudo iwconfig wlan0 essid ACCESSPOINT
sudo iwconfig wlan0 enc WEPKEY
sudo dhclient wlan0

---

### Post by Kobalt on 2007-03-25
If you don't see the applet in your notification area then log out and back in, network-manager starts automatically with your gnome session.

---

### Post by trevoore on 2007-03-25
Hi!

Unfortunately, when I try Alt-F2 with nm-Applet nothing happens. And when I restart my computer, which I have to do all the time anyway because Internet only works under Windows, then I don't have any Network Manager on the top right corner.
I tried re-installing (old Windows-reflex) but nothing changed. 

sigh.

t

---

