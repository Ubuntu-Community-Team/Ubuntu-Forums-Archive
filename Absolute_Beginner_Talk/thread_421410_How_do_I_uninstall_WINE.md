---
title: "How do I uninstall WINE"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-24
Hello:

Still new to Ubuntu. 
Well I tried WINE on Ubuntu, and successfully installed MS Word, but I don't know I really don't like it. A lot of the programs don't work, and it is pretty cumbersome to use. I think what I'm going to do is keep my dual boot, but increase my Ubuntu partition, and just use a very stripped down version of Windows as needed. So my question then is, how do I uninstall WINE on Ubuntu? I should mention my Ubuntu is 6.0.6.  Any help would be appreciated.

---

### Post by tomcheng76 on 2007-04-24
```
sudo apt-get remove wine
```
if you want to completely remove your wine application,use
```
sudo apt-get remove --purge wine
```

---

### Post by mlentink on 2007-04-24
But why would you want to? 
It's not as if it's in the way. like it would be in <cough>Windows</cough>. It6&#347; just sitting there, eating relatively little disk-space, waiting for you to get back for that one app you might want it to chew for you....

---

### Post by kpkeerthi on 2007-04-24
Also,
```
rm -rf .wine
```
from your HOME folder.

---

### Post by orwellus on 2007-04-24
Thanks for the info. I think dual boot is still best for me. I just don't like WINE. I think it has a way to go before it is a useful application. Maybe in a couple of years, I'll try downloading it again.

---

### Post by t00th on 2007-04-24
Another option to doing a dual boot is setting up a virtual machine with a program such as VirtualBox or VMware.  VirtualBox is the one I use, and is fairly easy to set up.  It basically runs another operating system inside of Ubuntu.  If you are interested, send me a message and I can send you a a link to a HOW TO guide.

---

### Post by zvacet on 2007-04-24
You can try this

[http://ubuntuforums.org/showthread.php?t=361528]("http://ubuntuforums.org/showthread.php?t=361528")

---

### Post by Calash on 2007-04-24
I use VMWare Server here.  Works great for most apps.  I still have to dual boot for some games I play....I want every ounce of performance I can get ;)

---

