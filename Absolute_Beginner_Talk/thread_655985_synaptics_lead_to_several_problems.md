---
title: "synaptics lead to several problems"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by eddiez on 2008-01-02
Hello guys, i just recently installed ubuntu on my box. Well, the first thing i did is installed wallpapoz just it seems to be missing python.imaging lib.  I then went to the synaptics package manager and the library didnt exist. so i downloaded a new synaptics manager version since i couldnt update my current synaptic manager and a other error came up the c++ compiler seemed to be missing aswell. I read different blogs none seemed to work and im out of ideas unto how to fix both these problems can someone help me ?

---

### Post by ~LoKe on 2008-01-02
It's unadvised to install a package outside of the repository unless you're sure of how it will integrate.  Upgrading Synaptic wouldn't give you any new packages.  Open the terminal and type the following:
```
sudo dpkg-reconfigure synaptic
```
I haven't had to do this in the past, but it should work.

---

