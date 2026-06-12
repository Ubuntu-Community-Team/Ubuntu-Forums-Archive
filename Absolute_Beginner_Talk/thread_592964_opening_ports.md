---
title: "opening ports"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by trynet on 2007-10-26
how do I open ports? 
I'm trying to get utorrent to work but I get really slow download speeds without the opened port.
how do I open a port?

---

### Post by Dr Small on 2007-10-26
Install Firestarter, the GUI of Iptables:
```
sudo apt-get install firestarter
```

Go to System > Administration > Firestarter, to configure it.

Dr Small

---

### Post by trynet on 2007-10-26
> **Dr Small said:**
> Install Firestarter, the GUI of Iptables:
```
sudo apt-get install firestarter
```

Go to System > Administration > Firestarter, to configure it.

Dr Small
ok then, that settles it, my system is screwed up -_-
```
E: Couldn't find package firestarter

```

---

### Post by scrooge_74 on 2007-10-26
Open synaptic, I dont remember but it could be that firestarter is in the other repositories and you have to enable them first

---

### Post by Pumalite on 2007-10-26
In Ubuntu the ports come closed by default, but every time you use an application that needs a port, a port is forwarded. You are still behind a firewall. Firestarter is just a front end for the IPTables that come installed by default with your Ubuntu.

---

### Post by llamakc on 2007-10-26
You need to enable the universe repositories in Synaptic/Adept.

---

