---
title: "canoscan 630p not working"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by roems on 2008-04-15
Hi all,

I am trying to use a canoscan 630p scanner with parallel port on a xubuntu 7.10 PC. Indeed it worked when I had installed xubuntu 6.10. I followed the same procedures in order to be able to scan with Xsane: 

I uncommented canon_pp on  /etc/sane.d/dll.conf and also uncommented the the line of 630pb file in  /etc/sane.d/canon_pp.conf.

When I checked if computer detected the scanner even in rood mode:

[SIZE="2"][FONT="Courier New"]scanimage -L[/FONT][/SIZE]

no device was detected.

However when I type[FONT="Courier New"][SIZE="2"] ls -l /dev/parport0[/SIZE][/FONT]
crw-rw---- 1 lp scanner 99, 0 2008-04-14 22:57 /dev/parport0

the scanner appears,

There is a message that could be the reason of the problem but I don't get it.
[FONT="Courier New"][SIZE="2"]
dmesg |grep parport0[/SIZE][/FONT]
[   28.288950] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   30.383848] lp0: using parport0 (interrupt-driven).

Any idea? Thanks beforehand for your help,

Roberto

---

### Post by spiderbatdad on 2008-04-15
you might read the output of ```
dmesg
```
I'm thinking you may need to add pci=routeirq to the kernel line of your boot menu.

---

### Post by Sef on 2008-04-15
Here's what the [Sane-Project]("http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=canoscan+630p&bus=any&v=&p=") says.

---

