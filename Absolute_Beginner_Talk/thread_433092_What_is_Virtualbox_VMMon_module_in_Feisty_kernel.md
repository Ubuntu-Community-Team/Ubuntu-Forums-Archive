---
title: "What is Virtualbox VMMon module in Feisty kernel?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-04
Hi,

I will soon recompile a Ubuntu Feisty kernel and I'd like to know what is the Virtualbox VMMon module found under "Ubuntu drivers/Ubuntu misc added drivers" in the kernel configuration? Currently it is set as a loadable module but should I compile it into the kernel if I intend to use VirtualBox???

Thansk

---

### Post by bodhi.zazen on 2007-05-04
VMMon is the magic that allows virtualization :)

IMO, You do not need to compile your kernel with VMMon. 

After you boot your new kernel, run this command to set up VirtualBox :

```
sudo /etc/init.d/vboxdrv setup
```

_Note_: sometimes I have needed to run this command twice to set up VirtualBox.

---

### Post by kilou on 2007-05-04
But I still need to install VirtualBox, right?

---

### Post by bodhi.zazen on 2007-05-04
I am not sure i follow you.

You will of course need to install Virtualbox if you intend to use it. Assuming VBox is already installed, I would not foresee the need to re-install VBox after compiling your kernel.

---

### Post by kilou on 2007-05-04
Ah OK I was just a bit lost. I already have VirtualBox installed but I thought that maybe with tha module activated I wouldn't need VirtualBox install anymore...but that's not the case.

Thanks for the help!

---

