---
title: "[SOLVED] What is the exact purpose of iptables?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by DBrocks on 2008-03-29
Hey everybody out there:
I am just getting my ubuntu-legs, and I have a question. It's probably really simple to most, but I don't quite understand iptables. I've seen several sites about them, but none of them really helped me. Please remember, I'm not a ubuntu genius, but I know what I'm doing for the most part. Any help is greatly appreciated. Thanks in advance!

~Dan

---

### Post by NightwishFan on 2008-03-29
Iptables is a firewall. You can download Firestarter as a gui method of configuring it but I have found that to be pretty useless in my case as all my ports are closed.

---

### Post by Joeb454 on 2008-03-29
As far as I'm aware, IPTables is a firewall, though there is no GUI for it (front-end app's do exist however).

I've never used it before, Firewall's tend to break if I fiddle with them ;)

---

### Post by DBrocks on 2008-03-29
Thanks guys. That's exactly what I needed to know. Short, sweet, and too the point!

---

### Post by mrsteveman1 on 2008-03-29
iptables is actually just the commandline interface for the kernel firewall and networking framework, netfilter.

There are a bunch of GUIs for the firewall, firestarter is one, but more simple if you just want to ensure there IS a firewall running, on hardy you can just open a terminal and type:

```
sudo ufw enable
```

This will enable the firewall by default, even through reboots. If you need more configuration you can install the GUI but most of the time it's not necessary, and some of the GUIs are simple config apps they don't actually ensure the firewall stays on after reboot.

---

