---
title: "Printer does not respond"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-07-19
i have Canon i560 printer, which works fine on my windows XP, but when i try to print via Ubuntu, it sends the "Print Job", but does not print anything

i tried to change the driver to S800, no change

---

### Post by bullgr on 2007-07-19
go there
[http://ubuntuforums.org/archive/index.php/t-10540.html](http://ubuntuforums.org/archive/index.php/t-10540.html)
it's about 2,5 years old but i believe (and hope) it will be working...

---

### Post by forestpixie on 2007-07-19
try this - it might help you

[http://doc.gwos.org/index.php/Canon](http://doc.gwos.org/index.php/Canon)

EDIT - I try for slow food too :D

---

### Post by Seisen on 2007-07-19
An easier way to do it is to follow my guide here [http://ubuntuforums.org/showthread.php?t=487890&highlight=canon]("http://ubuntuforums.org/showthread.php?t=487890&highlight=canon") except replace this in my guide

```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
``` with this

```
sudo apt-get install apt-get libcnbj-2.4 bjfilter-2.4 pstocanonbj
```

---

### Post by asakurax on 2007-07-19
none of the above worked

the printer is recognized by the Ubuntu, but the printing "job" just doesnt go into actual printing

---

### Post by Terl on 2007-07-19
Over at LinuxPrinting.org it is listed as only partially working.  Check this: [Canon i560]("http://openprinting.org/show_printer.cgi?recnum=Canon-i560")

---

