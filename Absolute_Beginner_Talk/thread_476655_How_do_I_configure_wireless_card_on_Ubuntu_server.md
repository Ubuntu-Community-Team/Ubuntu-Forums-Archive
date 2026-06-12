---
title: "How do I configure wireless card on Ubuntu server?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by waynepr72 on 2007-06-17
Hi there,

Can anyone please advise how to configure the wireless card via Ubuntu server?  I also want to install the gui to server, what us the apt-get for this one the wireless card is configured?

I have a WEP key set up on my router, but not sure how to configure this card via the command line y ou get when you install and run server.

Many thanks,

Wayne

---

### Post by quark_77 on 2007-06-17
Hi Wayne,

Assuming your card is working you need to do the following:
```
sudo nano /etc/network/interfaces
```

This file will have an entry for your wireless interface, which will be either wlan0, eth1, ath0 or something else (try iwlist scan to see which interfaces support scanning & therefore are wireless). Anyway, in this file below your definition for whatever your wireless is add this:
> iface wlan0 inet dhcp (wlan0 is the name of your interface, wlan0 is a common one. This line will already be in the file, perhaps preceded by an "auto wlan0").
wireless-mode managed
wireless-essid some_network_name
wireless-key hexadecimal key

Then restart your network daemon:
```
sudo /etc/init.d/networking restart
```
If you can find your ssid you'll see yourself being bound to an IP here.

To get a GUI you can do any one of the following:
```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```

Which fetches the appropriate desktop (Gnome, KDE or Xfce). Note this download is pretty huge...!

Hope this solves a few problems,

Edit: If your router supports it, WPA1/2 would be a good idea as it is more secure. The WEP algorithm isn't insecure however its implementation is, so it can be broken (something to do with the headers). Search the net for aircrack-ng to see how it's done. If you want to find out about WPA configuration it's all here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539).

Quark_77

---

