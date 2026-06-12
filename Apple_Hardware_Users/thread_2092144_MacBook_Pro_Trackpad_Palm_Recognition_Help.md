---
title: "MacBook Pro Trackpad Palm Recognition Help"
date: 2012-12-06
forum: Apple Hardware Users
---

### Post by machumamu on 2012-12-06
Ok, so I am trying to figure out how to have the trackpad on my MacBook Pro 8.1 Ubuntu 64bit to ignore my palm resting on the trackpad... Here's what I've tried:

```
matthew@MBPUBUNTU:~$ sudo cp /usr/share/X11/xorg.conf.d/50-synaptics.conf /etc/X11/xorg.conf.d/my-synaptics.conf
[sudo] password for matthew: 
cp: cannot create regular file `/etc/X11/xorg.conf.d/my-synaptics.conf': No such file or directory 
```

---

### Post by trogdor1138 on 2012-12-07
I believe that's because there isn't a '/etc/X11/xorg.conf.d/' directory in a fresh Ubuntu install. This page on the wiki explains where to place X configuration files, and the updated directory locations: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

I'm guessing you're following along with instructions from somewhere; could you post these or link to them?

---

### Post by machumamu on 2012-12-07
Worked. Thank you very much. :D

---

