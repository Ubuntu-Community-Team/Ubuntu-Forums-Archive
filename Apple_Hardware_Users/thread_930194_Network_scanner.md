---
title: "Network scanner?"
date: 2008-09-25
forum: Apple Hardware Users
---

### Post by Apocrathia on 2008-09-25
I've got a headless ubuntu 8.04 server with an HP Photosmart C3180 hooked up to it. I've got the printer published through CUPS and the card reader is easily mountable through AFP. No problem there. However, I don't know where to start with sharing the scanner or how I would even use it on the client side. Any ideas? Client computers would be running OS X 10.5.

---

### Post by BryannPaulaMelvin on 2008-09-26
[http://hplip.sourceforge.net/troubleshooting/scanning.html](http://hplip.sourceforge.net/troubleshooting/scanning.html)

the second paragraph

Note you might have to install hplip form sourceforge with cups I'm not sure ubuntu versions support this....it didn't when I set this up before. 

I did this on 606 back when I bought a C3140 and ubuntu's version didn't support it then.

---

### Post by matthewboh on 2008-10-07
I'm trying to do the same thing, but I'm getting a 404 error on the link.  Any other ideas?  Is this supported?

---

### Post by Apocrathia on 2008-10-28
anyone else got any ideas? (bump)

---

### Post by matthewboh on 2008-10-29
Sorry guys - completely forgot about this thread.  Anyway, I've got my C3180 up and running and scanning away!

This thread - although not geared to Ubuntu - works [http://www.linux.com/feature/57798](http://www.linux.com/feature/57798) 

Instead of doing all the makes, just do 

```
sudo apt-get install sane sane-utils
```

on both the server and any client / pc you want to use xsane with.

Just make sure to follow all the other instructions - works great!

---

### Post by matthewboh on 2008-11-08
Oops running into another problem.  I can scan, but then I can't print.  Anyone have any ideas?

---

