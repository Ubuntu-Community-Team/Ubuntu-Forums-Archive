---
title: "More OPera help(sort of)"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by SOG420 on 2006-03-14
I'm tring to install OPera and it is telling me that there is a dependecy confilict The needed package is  Package libqt3c102-mt any idea how I might procure it?
Thanks

---

### Post by skymt on 2006-03-14
The best way to install Opera isn't, in fact, the deb from the web site. I suggest either using [Automatix](http://ubuntuforums.org/showthread.php?t=138405) or the Opera apt server.

To add the Opera server to apt, open a terminal, enter "sudo gedit /etc/apt/sources.list" and add the following line at the bottom:
```
deb http://deb.opera.com/opera/ etch non-free
```
Then open System > Administration > Synaptic Package Manager, click reload, find opera in the list, and install.

---

### Post by traveller on 2006-03-15
[QUOTE=SOG420]I'm tring to install OPera and it is telling me that there is a dependecy confilict The needed package is  Package libqt3c102-mt any idea how I might procure it?
Thanks[/QUOTE]
Hello, right now I'm surfing with Opera thanks to Automatix! 

I want to install Opera 8.52. Help needed!
[http://www.ubuntuforums.org/showthread.php?t=142974](http://www.ubuntuforums.org/showthread.php?t=142974)

---

