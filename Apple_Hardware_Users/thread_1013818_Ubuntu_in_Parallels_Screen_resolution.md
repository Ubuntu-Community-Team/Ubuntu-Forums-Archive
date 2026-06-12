---
title: "Ubuntu in Parallels: Screen resolution"
date: 2008-12-17
forum: Apple Hardware Users
---

### Post by mathiasdk on 2008-12-17
Hi

I have just installed Ubuntu through Parallels Desktop on my Macbook (1. gen).

It works great, but there is something wrong with the screen resolution. There is 2-3 centimetres of black space around the screen.

I have tried this guide: [http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/) - but it doesn't help (seems like it is for Ubuntu 7.04)

Can anyone please help me?

//Mathias

---

### Post by cyberdork33 on 2008-12-17
what version of parallels, and have you installed parallels tools?

---

### Post by mathiasdk on 2008-12-17
> **cyberdork33 said:**
> what version of parallels, and have you installed parallels tools?

I use Parallels 3.0 biuld 5584 and yes, I have installed Parallels Image Tools.

---

### Post by cyberdork33 on 2008-12-17
> **mathiasdk said:**
> I have installed Parallels Image Tools.
That is something different. You need to install parallels tools in your Virtual Machine. This is basically a set of drivers to allow your guest OS to operate better in parallels.

While your VM is running, select "Install parallels tools" from your Mac menubar. This will mount a cdrom image in the guest (linux) and you can run the installer from there (with sudo!).

---

