---
title: "My nearly solved connection problem"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-12-03
In order to connect to the net (via my livebox modem) I have to type these 2 lines in a terminal each and every time I switch on my computer:

sudo su
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

The big issue is that other users who dont have my admin password cant connect.
Is there a way to make the effect of these 2 lines permanent so as to avoid the tedious routine. Or is there a way to automatically execute them on startup without my personal intervention???

Thanx

---

### Post by daimaru on 2007-12-03
add it as a executable bash script in /etc/init.d

---

### Post by SteelCore on 2007-12-03
Is there a guide or tutorial on how exactly I could do this?

---

### Post by st33med on 2007-12-03
actually, you might want to do this:
```
sudo gedit /etc/rc.local
```
And add:
```
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```
before exit0.

---

