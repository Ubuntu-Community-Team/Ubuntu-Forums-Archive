---
title: "networking icon"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-08-03
Hey guys,

I use wireless networking and the default networking icon that appears when you insert the wireless card is unwanted.  I like the other networking icon that can be added from: right-clicking on the panel>>>add to panel>>>network manager. 

How do i remove the icon that shows up automatically  when i insert my wireless card?

---

### Post by Hospadar on 2007-08-03
I believe you can uninstall network-manager to get rid of the one in the system try (the one in the top right corner is the one you want to get rid of right?)

```
sudo apt-get remove network-manager network-manager-gnome
```

I would make sure you connection is set up correctly before you uninstall this stuff because you connection will not automatically configure itself after you remove these things and if you want to change it you will have to reinstall these packages or hand edit /etc/network/interfaces if you want to change you connection (use a different wireless access point)

for an alternative you might also try wifi-radar
```
sudo apt-get install wifi-radar
```
I think it adds itself to the panel automatically but you may need to do it manually.  It provides the same sort of wifi network discovery as network-manager-gnome does.  you shouldn't need it though if you only use one wifi network.

---

### Post by happy-and-lost on 2007-08-03
I assume you're referring to nm-applet. If you use it to connect, you can't remove the icon, but if you use a different method to connect (such as wifi-radar), you can remove nm-applet from session startup in the system menu (Preferences --> Session)

---

