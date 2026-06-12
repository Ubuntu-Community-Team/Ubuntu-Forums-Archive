---
title: "How to install this patch for Exaile?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Dusk2k2 on 2007-05-25
I'm unsure of how to install this patch for exaile.  Visit [http://exaile.org/](http://exaile.org/) and on the first page, there is a link to a patch that will fix problems with finding album covers.  How do I install this patch?

---

### Post by Happy_Man on 2007-05-25
Like the good link says....
download it to your desktop. and open a terminal (system -> accessories -> terminal).
```
cd /usr/share/exaile
sudo bash
patch -p0 < /path/to/amazon_ecs40.path
```

---

### Post by Dusk2k2 on 2007-05-25
It seems to be more than copy and paste.  Each time I try to enter the commands, I get a message saying that there is no such file or directory.  Is there something else I am supposed to do?

---

### Post by Happy_Man on 2007-05-26
Aaand... did you install exaile first?
```
sudo apt-get install exaile
```

---

