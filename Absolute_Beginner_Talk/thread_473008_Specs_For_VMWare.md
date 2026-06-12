---
title: "Specs For VMWare"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2007-06-13
Id like to install said program but this pc was built on the cheap.
Sempron 2800, 512mb ram, Ati 9150 card, 80gb hdd.
Will VM run okay on that?
 When I tried it on my XP pc it ran fine but XP didnt like it. (Probably because I dedicated half my 1gb ram to it.)

---

### Post by Bachstelze on 2007-06-13
Yep, it will run fine. Just don't expect ultra-high performance ;)

---

### Post by Mac70 on 2007-06-13
Next question: Can VM be run on demand only, so its not using resources when not in use?

---

### Post by muguwmp67 on 2007-06-13
In VMware server, the virtual machine is not started unless you tell it to power on.  As long as you suspend/power off the virtual machine after using it, your resources should be as normal.

---

### Post by captlogic on 2007-06-13
Yes, VMware will only allocate the resources when you startup the Virtual Machine, not performance loss when it's not running.

---

### Post by anaconda on 2007-06-13
About same specs than in my machine, so it will run just fine..

Execpt that vmware still doesnt have good support for new kernels..eg. feistys kernel, and  it will slow it down a bit. Virtualbox doesnt have this problem, so you might want to try it instead.. for now.

---

