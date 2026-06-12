---
title: "Building deb package to automatic configure a specific internet connection."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2007-05-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/pcmciautils/+bug/99479](https://bugs.launchpad.net/ubuntu/+source/pcmciautils/+bug/99479) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi.
I am interested in building a deb package with all the configuration files needed to connect to my ISP and using my modem.

I think I dont need to compile any software. The deb package just have to copy some files to a specific path, and possibly append some text to a file that already exist in the system.

Also, as I need to use setserial, that package should be on the requisits.

After this being done and tested for my specific modem and to my ISP, I would like to make it work with other modems and other ISPs.

What is the simpler way to do this?

---

### Post by Carlos Santiago on 2007-05-31
All I want is to make a deb package that after a double click, places the configuration files where they should be.

---

### Post by Carlos Santiago on 2007-05-31
Please help, this should be easy!

---

### Post by MinstrelBoy on 2007-05-31
Try   dh-make

[http://packages.ubuntu.com/feisty/devel/dh-make](http://packages.ubuntu.com/feisty/devel/dh-make)


Cheers
MB

---

### Post by Carlos Santiago on 2007-07-17
Done.

Check [http://www.guiaubuntupt.org/files/debs/kanguru_0.1.deb](http://www.guiaubuntupt.org/files/debs/kanguru_0.1.deb)

This DEB package configures the connection to Portuguese Optimus Telecom ISP (Kanguru), when using Novatel Merlin U630 PCMCIA modem.

---

