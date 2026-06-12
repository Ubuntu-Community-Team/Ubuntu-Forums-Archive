---
title: "Showing multiple wireless networks"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-07
Hello,

In the student's house where I live, multiple wireless networks are available. I have dual boot laptop, Win XP / Ubuntu. Both of them automatically pick the exactly the same network, however this is not the best one. In windows, I can click "show available wireless networks" and then 6-7 networks appear, from which I can pick which I like. However, I don't know how to do thing like that in Linux, so I have to work with this slow network. How can I deal with that? if there's something graphical available to click, I'd prefer it over terminal orders, because German letters in network names are not properly recognized (despite updates).

Thanks iin advance :)

---

### Post by Bachstelze on 2007-04-07
I usually use the command line for that but if I recall correctly, Ubuntu has a GUI tool for it. Open a terminal and do :

```
sudo apt-get install network-manager-gnome
```

If you're using Gnome or 

```
sudo apt-get install knetworkmanager
```

if you're using KDE.

---

### Post by O-pos on 2007-04-08
I have GNOME, I tried but apparently it doesn't work:

sudo apt-get install knetworkmanager

wacho@wacho:~$ sudo apt-get install network manager gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network
wacho@wacho:~$

---

### Post by Hieronymus on 2007-04-08
You can chose your network manually by using the commands:

```

iwlist eth1 scan [to find the networks]
iwconfig eth1 essid networkname [to select access point]
iwconfig eth1 enc encryptionkey [to set the key]

```

These settings will be lost though after reboot. Also you can goto System >> Administration >> Network and setup your wireless network card instead of using roaming mode. 

A 3th option is to just chose the network by using  the  network monitor.

Jeroen

---

### Post by O-pos on 2007-04-08
> **Hieronymus said:**
> You can chose your network manually by using the commands:

```

iwlist eth1 scan [to find the networks]
iwconfig eth1 essid networkname [to select access point]
iwconfig eth1 enc encryptionkey [to set the key]

```

These settings will be lost though after reboot. Also you can goto System >> Administration >> Network and setup your wireless network card instead of using roaming mode. 

A 3th option is to just chose the network by using  the  network monitor.

Jeroen

Thanks, but network names containing German letters ä,ö,ü have recognition problems if I'm writing. That's I want option to pick the network by just clicking on the name what already is written.

I managed to install GNOME network manager. but I can't find where's it installed. Any  ideas?

---

### Post by Hieronymus on 2007-04-08
> **O-pos said:**
> Thanks, but network names containing German letters ä,ö,ü have recognition problems if I'm writing. That's I want option to pick the network by just clicking on the name what already is written.

I managed to install GNOME network manager. but I can't find where's it installed. Any  ideas?

Right mouse button on the panel, add to panel, network monitor. It will appear into you systray.

Jeroen

---

### Post by O-pos on 2007-04-08
wow, it looks promising :) how to screen all available networks with it (network monitor)? I mean is there an option like "show all available networks"?

---

### Post by Hieronymus on 2007-04-08
> **O-pos said:**
> wow, it looks promising :) how to screen all available networks with it (network monitor)?

When you click on it it shows the available networks, also you can click on it and chose "connect to other wireless network", if it doesn't show anything then check via commandline with the command "iwlist eth1 scan"

Jeroen

---

### Post by O-pos on 2007-04-08
there are just two options across "name": "lo" and "eth1". these are not network names. there are 5-6 networks here.. Baybe you have Ubuntu other than 6.10?

"iwlist eth1 scan" shows only single - current network. If I restart to windows, then there are 5-7 networks.

---

### Post by Hieronymus on 2007-04-08
Oh, I'm sorry, I'm using feisty fawn, this has an more advanced version of network monitor. But in that case you can't scan with it for networks. I don't know why it doesn't see all networks, possibly because their signal strength is to low.  

Jeroen

---

### Post by O-pos on 2007-04-08
:( so then best choice should still be the Gnome Network Manager..

---

### Post by Hieronymus on 2007-04-08
Probably, or upgrade to feisty which will become stable on the 19th of this month. Although for me it is already stable. The upgrade is very simple achieved  anyway. 

But with the system >> administration >> network all should work fine as well, but I must still search for the network yourself in that case. 

Jeroen

---

