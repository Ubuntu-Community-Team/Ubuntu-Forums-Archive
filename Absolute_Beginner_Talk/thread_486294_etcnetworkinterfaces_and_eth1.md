---
title: "/etc/network/interfaces and eth1"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by slackorama on 2007-06-27
I have a wireless card in my laptop that shows up as eth1 when I run iwconfig yet it's not listed in /etc/network/interfaces (only lo and eth0 are listed there).  

Is this a problem?  Should I add it to /etc/network/interfaces?  

wifi isn't working for me is why I ask.

TIA.

---

### Post by DSn0wMan on 2007-06-27
Yes you will need to add it to the interfaces file. Make sure it has an "auto up" statement similar to lo and eth0.
Then you will need a reboot.

---

