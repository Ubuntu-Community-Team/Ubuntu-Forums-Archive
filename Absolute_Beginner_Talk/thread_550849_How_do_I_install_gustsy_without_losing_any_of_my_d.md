---
title: "How do I install gustsy without losing any of my docs settings and configurations?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-14
I don't see an option in the installer for upgrading. How would I go about doing this?

---

### Post by Ink-Jet on 2007-09-14
```
sudo apt-get dist-upgrade
```
If I'm not mistaken.

---

### Post by swoll1980 on 2007-09-14
When I do that the only thing it wants to upgrade is my ndiswrapper

---

### Post by SOULRiDER on 2007-09-14
Thats ebcause Gutsy is not out yet, whats there is BETA software. When the final version is out you will be prompted if you want to upgrade.

---

### Post by mikeyphi on 2007-09-14
I don't think you can "upgrade" to gutsy until the official release in October.

---

### Post by bodhi.zazen on 2007-09-14
To upgrade to Gutsy : [http://www.ubuntu.com/testing/tribe3](http://www.ubuntu.com/testing/tribe3)

---

### Post by swoll1980 on 2007-09-14
Thanks

---

### Post by swoll1980 on 2007-09-14
How do I install update-manager 0.59.23? I tried enabling proposed repo and search for it in synaptic no luck

---

### Post by bodhi.zazen on 2007-09-14
> **bloor75 said:**
> How do I install update-manager 0.59.23? I tried enabling proposed repo and search for it in synaptic no luck

:lolflag:



Add this to your repos :

> # Feisty-proposed, added to upgrade to Gutsy

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

Open a terminal, enter :```
gkso gedit /etc/apt/sources.list
```

Add those lines at the end of the file, save and exit.

Then : ```
sudo apt-get update
```

Then upgrade (via synaptic ... )

======

You may want to back up first, possibly with partimage :

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

You may want to move /home to it's own partition: # Makes it easy to re-install w/o loosing data in /home

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

