---
title: "Ubuntu Studio and some problems"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by xadloki on 2007-10-26
I figured I'd give a try at Ubuntu Studio this weekend and installed it, since I do video editing and photography it has the software I need.
I ran into some problems though...

These were the first things I did after a clean install. 
Setup network, install Nvidia drivers, downloaded updates and installed them.

First problem is when installing audacious-plugins from updates it shows me the following error:

E: /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu4_amd64.deb: trying to overwrite `/usr/lib/audacious/General/libcurl.so', which is also in package audacious-plugins-extra

Then it reports some error with openoffice things and leaves them unchanged... this probably is because the open office is not installed.

Third issue is that after trying out Ubuntu 7.10 386 (my processor is AMD64 and Ubuntu Studio version 7.10 AMD64) the desktop and aplications seems to react slowly and loading takes a few seconds unlike in Ubuntu where it's almost instant after clicking.
I don't know if this is specific to the Studio or would it seem slow even in regular Ubuntu AMD64 since I only tried 386 version.

Any advice on these issues ?

---

### Post by Dr Small on 2007-10-26
Personally, I would try a fresh install.

---

### Post by por100pre1 on 2007-10-26
Try this:

```
sudo apt-get remove audacious-plugins-extra
```

try the updates and then try to install them back again


```
sudo aptitude install ubuntustudio-audio
```

---

### Post by xadloki on 2007-10-27
thanks for the advice, however I decided to switch back to plain ubuntu and install the needed packages before trying to solve the issues.

---

