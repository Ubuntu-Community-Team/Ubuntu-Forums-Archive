---
title: "powerbook g4 problem"
date: 2008-06-21
forum: Apple Hardware Users
---

### Post by bobocbbb on 2008-06-21
hello all,
 
i am new to ubuntu and i have a powerbook g4 ppc.
i have the ppc version from ubuntu and i made 2 partition 1 for osx and 1 for ubuntu,dual boot.
the problem is i can not configur the wireless card to work,i have downloaded the b43xx fwcutter driver for ppc installed it and still does't work.
after all this i have another problem,my trackpad stopped working,i must plug an usb mouse to work with it.
 
can anyone help me?i am writeing from my imac,i need internet on my powerbook to.

---

### Post by owlgorithm on 2008-06-27
Use
```

sudo aptitude install b43-fwcutter

```
instead :-)

---

### Post by owlgorithm on 2008-06-27
You may also want to check out the following thread:
[http://ubuntuforums.org/showthread.php?t=802528]("http://ubuntuforums.org/showthread.php?t=802528")

It sounds like a problem with your /etc/X11/xorg.conf file, and your answer may already be in the above thread.

---

