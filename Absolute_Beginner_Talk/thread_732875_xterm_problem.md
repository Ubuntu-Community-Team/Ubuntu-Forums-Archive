---
title: "xterm problem"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by D330191 on 2008-03-23
i am a newbie using ubuntu, and i am trying to install video and audio codects using xterm. problem is, when ever i enter the command line;
sudo apt-get install .......
NO matter what i type in after that, it comes up with the same answer...package cannot be found.
Help...PLEASE?

---

### Post by zerhacke on 2008-03-23
use apt-cache search to find the package first.

---

### Post by Dr Small on 2008-03-23
> **zerhacke said:**
> use apt-cache search to find the package first.
+1
```
apt-cache search *appname*
```

Once you find it, simply run:
```
sudo apt-get install *realappname*
```

Dr Small

---

### Post by mali2297 on 2008-03-23
Why don't you use **Synaptic**? (It has a search function.)

You probably want to install ubuntu-restricted-extras. In Synaptic, go to *Settings -> Repositories* and check that you have the *universe* and *multiverse* repositories enabled. Then search for the package *ubuntu-restricted-extras* and install.

---

### Post by D330191 on 2008-03-24
Thanx alot guys, i finally got the problem solved. seems like i needed to enable the universe and multi universe, then alot of downloading ensued.

---

