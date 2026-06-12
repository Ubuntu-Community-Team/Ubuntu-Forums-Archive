---
title: "I've got another question. XFCE"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-20
How do I install it on my Kubuntu installation. I searched in Adept but there was quite a few packages for it there. I was thinking Xubuntu-desktop but I couldn't see it in the package list.

---

### Post by etc on 2005-12-20
Uncomment the universe repos in your /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu breezy universe
```
then
sudo apt-get update
sudo apt-get xubuntu-desktop

---

### Post by Rackerz on 2005-12-20
Will that install the latest XFCE?

---

### Post by aysiu on 2005-12-20
[QUOTE=Rackerz]Will that install the latest XFCE?[/QUOTE] The latest? It'll install 4.2.2. Is that recent enough for you?

---

### Post by Rackerz on 2005-12-20
Hmmmmm. If I was testing this, I tried to do sudo apt-get remove xubuntu-desktop to see if it would get rid of all the XFCE stuff, but it didn't. I have loads of it in the menus. How can i get rid of it?

---

### Post by aysiu on 2005-12-20
Try this, and let me know if it works. If it does, I'll make it into a HowTo: Open up a terminal and paste this command in ```
sudo apt-get remove gtk2-engines-xfce libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfceutil-1 libxfcegui4-3 xfce4 xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-iconbox xfce4-icon-theme xfce4-mcs-manager xfce4-mcs-plugins xfce4-panel xfce4-panel-menu-plugin xfce4-session xfce4-showdesktop-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xubuntu-desktop xubuntu-artwork xubuntu-artwork-usplash
```

---

### Post by Rackerz on 2005-12-23
It doesn't work .. it says it can't find a package;

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxfceutil-1

---

### Post by fuscia on 2005-12-23
are you sure you still have it anywhere else besides your menus?

---

### Post by 5-HT on 2005-12-23
[QUOTE=Rackerz]It doesn't work .. it says it can't find a package;

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxfceutil-1[/QUOTE]

I'm running XFCE and couldn't find libxfceutil-1, but I do have libxfce4util-1 installed...

So if you're looking to remove it, hopefully that should work (if it got installed originally).

HTH

---

