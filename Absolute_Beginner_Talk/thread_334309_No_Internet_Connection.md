---
title: "No Internet Connection"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by UKPunk on 2007-01-08
Hi everyone,
I've installed Ubuntu 6.06 with the CD and everything went well but I have no internet connection. My connection is wireless using an Inventel UR054g (R01) V1.1 modem via an Orange livebox.
In Network settings>Connections>Wireless connection it says "The interface eth2 is active". In Connection settings the configuration is DCHP and the connection is enabled. The default gateway device is eth2.
The question is, what am I doing wrong or maybe not doing that I need to do to get connected?
Thanks in advance for your patience with and advice for this most absolute beginner.

---

### Post by ajmorris on 2007-01-08
go to a command line and type [PHP]sudo dhclient[/PHP]

See if that helps.

---

### Post by punx45 on 2007-01-08
you most likely need to install some proprietary drivers for your wireless adapter.   I would search the forum, and then the internet at large for information on using your specific model adapter with linux.

---

### Post by UKPunk on 2007-01-08
Thanks AJ and punx45. I'll do that tomorrow.

---

### Post by harmeet on 2007-01-08
I had the same problem. Assuming your wireless card is detected properly. Install network-manager if you don't already have it. To find out -

[LIST=1]
[*]See on the panel if it is there. It looks like "Network Monitor" but it is not the same. 
[*]Right click on the panel and select "Add to panel"
[*]See if you can find "Network Manager" icon.
[/LIST]

You can install it by running this command -

```
sudo aptitude install network-manager
```

After that click on Network Manager icon on the panel and select "Connect to Other Wireless Network..."

It will bring you a UI which asks the network name and password etc.

Hope it helps.

---

