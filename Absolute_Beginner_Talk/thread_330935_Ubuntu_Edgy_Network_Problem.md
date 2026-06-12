---
title: "Ubuntu Edgy Network Problem"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by NEvolution on 2007-01-03
Hi, I've just installed Edgy and updated everything through a wired connection.

Now I am trying to get the wireless to work using wifi-radar.

It correctly connects and gives me an IP through DHCP. But when trying to connect to the Internet using Firefox, it just keeps loading and eventually times out.

The weird thing is that wireless Internet worked when I tried this using the LiveCD when I still had Windows installed. And now it just doesn't work.

Any ideas?

---

### Post by riven0 on 2007-01-03
Are you are sure you have the correct drivers installed? Does your card require the ndiswrapper? If not, try to download network manager. Perhaps that'll solve your problems:
> 
sudo apt-get install network-manager

---

### Post by zmuth734 on 2007-01-03
Do you have a WEP key you forgot to type in maybe?

I've had some problems with wifi radar.
I've had better luck installing wlassistant and using: 
```
sudo wlassitant
```, works fine for me

---

