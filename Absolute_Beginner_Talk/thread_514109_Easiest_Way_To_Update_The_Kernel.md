---
title: "Easiest Way To Update The Kernel"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-07-31
How do I update [this computer]("http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&highlightOption=107558&PRODUCT_ID=109506&DISC_MODEL=0#0") to a newer kernel? It currently has 2.6.20-16 on it and it has problems hibernating therefore I want to update the kernel.

The problem is that the processor is too slow to compile the kernel from source.

Is there like a .deb package to install the kernel from suited for my processor type? Probably that would be over-simplifying :D

And, btw, what is my processor type? I am guessing i686? Can't be sure...

Thanks a lot.

---

### Post by AnRa on 2007-07-31
> **Majorix said:**
> The problem is that the processor is too slow to compile the kernel from source.You have to be more patient! ;)

---

### Post by testube_babies on 2007-07-31
Easiest way:  wait for next Ubuntu release

Next easiest way:  switch to a distro with rolling updates

Hard way:  compile it yourself (and wait a few hours for it to finish :))
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

And yes, you have i686.

---

### Post by walkerk on 2007-07-31
The easiest way without waiting for Gutsy.. I did the following and now Feisty with 2.6.22-9-generic (from Gutsy repos)

[Check out my thread for instructions...]("http://ubuntuforums.org/showthread.php?t=511974")

Enjoy :)

---

### Post by testube_babies on 2007-07-31
> **walkerk said:**
> ```
sudo gedit /etc/apt/sources.list
```

```
**gksudo** gedit /etc/apt/source.list
```
[See [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) for more info]

...and good idea, btw, to take the kernel from the gutsy repos.  However, it's generally not recommended to mix repos/packages from different releases, since you are effectively running a mix of releases that is neither supported nor tested.  But if it works, why not :)?  Commenting out the gutsy repos at the end should avoid most problems, anyway.

---

### Post by Majorix on 2007-07-31
Ok thanks very much, I updated following walkerk's guide.

I will do some testing now and let you know how it goes. Everything seems ok so far though.

Thanks again walkerk.

---

### Post by walkerk on 2007-07-31
no problem :)

---

