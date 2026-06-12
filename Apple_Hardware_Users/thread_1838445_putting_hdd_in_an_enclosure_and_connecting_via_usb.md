---
title: "putting hdd in an enclosure and connecting via usb"
date: 2011-09-03
forum: Apple Hardware Users
---

### Post by virens on 2011-09-03
hi, i have an ubuntu installation on an old desktop. if i take out the hard drive and put it in an enclosure so i can connect it to my macbook via usb. will i be able to boot into ubuntu by press the option key at startup or do i need to do anything to allow me to do this?

---

### Post by DoubleClicker on 2011-09-03
Macbooks will only boot from drives with GUID partitions.  There are several utilities that will convert MBR partition tables to GUID partition tables ( iPartition is the one that imediatly comes to mind).

You should also install rEFIt on your Macbook.

---

