---
title: "Firewall"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Nezing on 2007-06-01
Maybe this has been covered before,but for a "newbie" like myself,how do I set up a firewall in Ubuntu?
I have downloaded nufw 2-2-0,and stored it in a folder on my desktop.I know I have to use Terminal,but what commands do I type?](*,)

---

### Post by alienexplorers on 2007-06-01
iptables is a firewall in ubuntu that runs constantly.  No need for anything else.

---

### Post by wormser on 2007-06-01
You can install Firestarter to manage iptables.

```
sudo apt-get install firestarter
```

---

### Post by Marsolin on 2007-06-01
I'd recommend installing [Firestarter]("http://linuxappfinder.com/package/firestarter") or [Guarddog]("http://linuxappfinder.com/package/guarddog"). Both are GUI's for configuring iptables.

---

### Post by Nezing on 2007-06-01
Thanks guys.I just downloaded Firestarter,and it set up perfectly.Panic over.:popcorn:

---

