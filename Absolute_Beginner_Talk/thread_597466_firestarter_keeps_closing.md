---
title: "firestarter keeps closing"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by mary.sixty on 2007-10-30
I have installed firestarter.  but every time I start it, it will run for 1-5 minutes then shuts down.

---

### Post by khurrum1990 on 2007-10-30
Hi, firestarter just needs to be configured once and u don't need to turn on the main gui for starting the firewall as all it is a gui for configuring iptables. Though I would suggest that u try reinstalling it or configure it again.

---

### Post by julian67 on 2007-10-30
[ How-To: Firestarter on startup (better & safer way)]("http://ubuntuforums.org/showthread.php?t=542756")> This how-to will let you start Firestarter automatically without having to enter a password for it, but also not editing /etc/sudoers and, thus, giving access to anyone to change it.


If you configure firestarter but don't start it on reboot it does nothing. iptables rules revert to default, i.e. all traffic allowed, until firestarter is up. The method in the link above is very good and allows firestarter's rules to be loaded automatically without the gui needing to be run.

---

### Post by mary.sixty on 2007-10-30
I installed firestarter because I wanted:
Real-time firewall event monitor shows intrusion attempts as they happen
View active network connections
I also liked the looks of the "lock firewall"
But if I have to restart it every couple of minutes because it keeps shutting down, then that's not going to be worth the trouble.  I tried reinstalling and reconfiguring it.  No difference.

---

### Post by aidanr on 2007-10-30
Yeah I noticed this earlier, just tried to recreate it there and it closed itself, messages.log says it segfaulted
```
Oct 31 00:52:15 aidan-desktop kernel: [10023.321920] firestarter[7757]: segfault at 0000000000000048 rip 00002baa0541bc2a rsp 0000000041001080 error 6
```

---

