---
title: "USB scanner not detected"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2006-12-27
I have a "Mustek bearpaw 2400ta plus" i attached it to my computer and nothing happened 
i tried xsane but it said no devices found kooka just sat there im running Kubuntu 6.10 and need to scan some important papers please help!

---

### Post by tagra123 on 2006-12-27
> **wert613 said:**
> I have a "Mustek bearpaw 2400ta plus" i attached it to my computer and nothing happened 
i tried xsane but it said no devices found kooka just sat there im running Kubuntu 6.10 and need to scan some important papers please help!

try running

sudo xsane 


from a terminal.

If that works than you cans change a couple of items in the init scripts to set permissions correctly at startup -- I think that's what I did. 

Also googling for sudo xsane may help.

---

### Post by alienexplorers on 2007-02-06
Did you also select libsane and libsane-extras.

---

