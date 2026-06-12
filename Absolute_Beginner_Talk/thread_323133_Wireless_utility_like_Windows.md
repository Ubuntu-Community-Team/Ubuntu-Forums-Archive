---
title: "Wireless utility like Windows?"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-12-21
In windows I can easily check the local networks and connect to them without putting in my WEP every time because it remembers that. With Ubuntu I have to know the name and WEP of whatever network I'm trying to connect to. Is there a program that'll make wireless connecting simpler like it is in windows?

---

### Post by aysiu on 2006-12-21
I think there's one called NetworkManager:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

I don't have wireless yet, so I don't know all the details.

This is something that's one of the top priorities to fix in Ubuntu's next release, Feisty Fawn:
[https://blueprints.launchpad.net/distros/ubuntu/+spec/network-roaming](https://blueprints.launchpad.net/distros/ubuntu/+spec/network-roaming)

---

### Post by macogw on 2006-12-21
Yeah, use Network Manager and nm-applet.  The applet will have a little dropdown listing all the nearby wireless networks.  You can grab an unprotected one or you can save the WEPs to your "keyring" for revisiting the same wireless connection.  That fix is about roaming between wireless networks so it just grabs the ESSID instead of you having to know them.  It'd also have those packages (and wpasupplicant, I think) installed by default so the day I spent configuring mine doesn't need to be repeated.

---

### Post by HokeyFry on 2006-12-21
try wifi-radar, its available in the ubuntu repos

---

### Post by mexlinux on 2006-12-21
wlassistant

---

