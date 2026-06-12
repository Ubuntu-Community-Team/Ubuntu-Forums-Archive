---
title: "[SOLVED] Uninstalling MoBlock"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by H3retic on 2007-12-12
How do I uninstall Moblock?  It's blocking google and making my internet misbehave.

---

### Post by bodhi.zazen on 2007-12-12
```
sudo apt-get remove --purge moblock
```

I think it leaves a config file in /etc or /etc/moblock that also has to be removed (manually)

```
sudo rm -rf /etc/moblock
```

---

### Post by H3retic on 2007-12-12
chris@chris-ubuntu:~$ sudo apt-get remove --purge moblock
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Does not work in normal console or root console :(
Then again, Moblock is currently working and starting with the session, and I don't know how to remove it or turn it off.

help!

---

### Post by bodhi.zazen on 2007-12-12
Do you have ADD/Remove programs or synaptic running ? If so you need to close them first.

---

### Post by H3retic on 2007-12-12
**SOLVED**

Thanks!

---

