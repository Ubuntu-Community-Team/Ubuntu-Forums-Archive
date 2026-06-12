---
title: "how to set custom resolution in VMware"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by hatchetman82 on 2007-01-20
Hello.

i have the latest stable version (6.10) up and running in vmware (just finished installing it and updating it, havent touched anything betond the install defaults).

its running on a laptop that has a screen resolution of 1440x900, which does not appear as an option in the system --> preferences --> screen resolution.

all of the stuff i find by looking for similar problems on the forum involves installing display drivers, which im not sure is right for my problem (because ubuntu is running inside a virtual machine, which i think means it sees some sort of generic display card rather then the physical one i have).

so what are my options in getting ubuntu to utilize the full screen area ?
thanks in advance for any answers / clues / directions / attempts.

---

### Post by Jussi01 on 2007-01-20
Check out the instructions for vmware in this thread.

[http://www.ubuntuforums.org/showthread.php?t=341875](http://www.ubuntuforums.org/showthread.php?t=341875)

HTH

---

### Post by hatchetman82 on 2007-01-20
thank you for the link.

eventually, this worked :
```

sudo dpkg-reconfigure xserver-xorg

```

---

