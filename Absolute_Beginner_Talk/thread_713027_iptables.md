---
title: "iptables"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by kelinu on 2008-03-02
Hi,
I've heard that Ubuntu has a firewall called iptables...How do I open this program and does it have a GUI? I would like to know this as i think it is firewalling a few things that I want to allow.

Thanks,
Michael

---

### Post by Oldsoldier2003 on 2008-03-02
> **kelinu said:**
> Hi,
I've heard that Ubuntu has a firewall called iptables...How do I open this program and does it have a GUI? I would like to know this as i think it is firewalling a few things that I want to allow.

Thanks,
Michael
You can install firestarter, a Gui-frontend (for gnome) to configure your iptables I think the KDE GUI frontend fro iptables is called guarddog. ANothe option is to install bastille, which is a hardening tool that als sets up your iptables.

firestarter:

```
sudo apt-get install firestarter
```


bastille:

```
sudo apt-get install bastille
```

---

### Post by kelinu on 2008-03-02
ok i researched these i think ill get guarddog ...can u explain to me what bastille is i didnt really understand

---

### Post by Oldsoldier2003 on 2008-03-02
> **kelinu said:**
> ok i researched these i think ill get guarddog ...can u explain to me what bastille is i didnt really understand

bastille is a script that asks you some questions about how you would like to harden your system to make it more secure. If you answer yes to ip filtering it will also set up your iptables rules.

---

