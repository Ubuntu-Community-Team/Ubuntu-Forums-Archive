---
title: "Install Qemu Launcher&gt;"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-11-09
Anyone know ow to install qemu launcher

---

### Post by Ecthelion on 2006-11-10
What about synaptic Package manager?

>System > Administartion > Synaptic Package Manager

Use the search option and install...

Or you can do

```
sudo apt-get install qemu 
```

Make sure you have the universe backports enabled or it won't appear anywhere...

---

### Post by Marsolin on 2006-11-10
[Qemu Launcher]("http://linuxappfinder.com/package/qemu-launcher") isn't in the Ubuntu repositories, but it is in Debian etch. You could try grabbing that deb file and installing it.

---

### Post by spyker3292 on 2006-11-10
It says dependancy not satisfiable: qemu

---

### Post by Marsolin on 2006-11-10
It looks like it will work with the version of [QEMU]("http://linuxappfinder.com/package/qemu") in Edgy, but now Dapper, although you could try to force the install using apt-get. Running [Qemuctl]("http://linuxappfinder.com/package/qemuctl") as an alternative to [Qemu Launcher]("http://linuxappfinder.com/package/qemu-launcher"). It is dependent upon a lower version of QEMU.

---

### Post by spyker3292 on 2006-11-10
> **Marsolin said:**
> It looks like it will work with the version of [QEMU]("http://linuxappfinder.com/package/qemu") in Edgy, but now Dapper, although you could try to force the install using apt-get. Running [Qemuctl]("http://linuxappfinder.com/package/qemuctl") as an alternative to [Qemu Launcher]("http://linuxappfinder.com/package/qemu-launcher"). It is dependent upon a lower version of QEMU.

How do you run qemuctl I got it installed

---

### Post by spyker3292 on 2006-11-11
bump

---

### Post by Marsolin on 2006-11-11
Run "man qemuctl" from the command line for details. Have you tried typing qemuctl into the Run command dialog box?

---

