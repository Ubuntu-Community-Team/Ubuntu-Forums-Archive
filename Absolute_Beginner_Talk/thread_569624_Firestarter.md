---
title: "Firestarter"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by LaDeDa on 2007-10-07
For whatever reason, I installed the package, however, some options do not seem to work.  
For example, I checked the option to load on startup, but it doesn't load (at least the icon doesn't show up).
I checked ICMP, but left unchecked all the options below.  According to "Shielsup", it still gets a "ping" response from my system.  Anyone have an idea of what's going on here ??

---

### Post by Dr Small on 2007-10-07
Firestarter is just the GUI of iptables. Just because you don't see it, doesn't mean iptables isn't running. You do not need nautilus up all the time to check and see if you have a filesystem...

You can setup policies in firestarter, which in turn changes it in iptables for you.

Dr Small

---

### Post by n3tfury on 2007-10-07
> **Dr Small said:**
> Firestarter is just the GUI of iptables. Just because you don't see it, doesn't mean iptables isn't running. You do not need nautilus up all the time to check and see if you have a filesystem...



no, you don't, but it makes sense that it would show up in the panel so you can quickly add/remove/modify iptables in an instant.

---

### Post by ayenack on 2007-10-07
If you want to see if Firestarter is running type this in terminal.

**sudo /etc/init.d/firestarter status**

If Firestarter detects an active network connection on startup it'll start automatically.
If you want Firestarter to start the GUI follow this guide.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_IPtables_Firewall_Configuration_GUI_.28Firestarter.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_IPtables_Firewall_Configuration_GUI_.28Firestarter.29)

Scroll down to  How to make the Firestarter GUI start automatically at startup.

Not secure though.

In regards to replying to a ping make sure you have Drop Silently selected under Advanced Options. And turn of ICMP if your not using it. Also turn on Block broadcasts from external network. If they're not on.

---

