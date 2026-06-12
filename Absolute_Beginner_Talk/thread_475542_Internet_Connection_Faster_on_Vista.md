---
title: "Internet Connection Faster on Vista"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-16
It's a VERY noticeable difference.
My internet connection IS faster on Vista.
Anyone have any ideas?

L1 Attansic Ethernet

---

### Post by starcraft.man on 2007-06-16
> **dannymichel said:**
> It's a VERY noticeable difference.
My internet connection IS faster on Vista.
Anyone have any ideas?

L1 Attansic Ethernet

Are you talking about how fast pages load? I never noticed a difference but others have said firefox is slower on Ubuntu. If you mean raw download speed, afraid I don't know whats wrong. Long as its a generic ethernet line there isn't a reason for it not to give you a maximum speed. Maybe someone else more knowledgeable knows...

---

### Post by dannymichel on 2007-06-16
I think I mean both. :/

---

### Post by dunedust on 2007-06-16
Have you tried blacklisting ipv6?

```
sudo gedit /etc/modprobe.d/blacklist
```

add this to the file

```
blacklist ipv6 
```

save and reboot

You can also try using open dns

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by Golyadkin on 2007-06-16
I haven't changed anything about ip settings or network settings in Ubuntu, and I get the exact same speed and performance in Ubuntu as I used to get in XP. I am using the onboard gigabit LAN of my MSI K9N Neo-F motherboard.

Do you have the relevant ports forwarded if you mean downloading with P2P programs?

---

