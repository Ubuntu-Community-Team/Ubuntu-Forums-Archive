---
title: "How much resources is needed to run Ubuntu over Freebsd"
date: 2017-12-25
forum: BSD
---

### Post by x3ua on 2017-12-25
Freebsd and openbox. If I run Ubuntu on VM, how much resources I need? 

I bought HP envy 13", i5, 8Gb DDR3, 256 m2 SSD

Is there enough memory to VM?

---

### Post by spjackson on 2017-12-28
In short, I think the answer is "yes". The minimum amount of resource you need to allocate to your VM depends which desktop flavour you want to use and what you want to do with it. However, 2Gb of RAM would probably be enough. For disk space, you can quite easily get away with 8-10Gb, but more if you need a lot of data. Number of cores? Again it depends what you want to do. In my experience it can run with just 1, but I tend to use lightweight desktops in a VM.

---

### Post by SeijiSensei on 2017-12-28
I use 2 GB for Linux VMs with a GUI. For servers half that should be plenty depending on the services offered. For Windows VMs I usually allocate 3-4 GB.

---

