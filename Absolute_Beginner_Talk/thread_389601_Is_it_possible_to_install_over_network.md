---
title: "Is it possible to install over network?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-03-20
I want to install ubuntu, but I'm having trouble because my CD drive is old so when I try to install it keeps reading files as corrupt even though I know the CD is fine.

My question is, is there any way to install ubuntu like Debian where I can do a network install?

---

### Post by K.Mandla on 2007-03-20
Yup. There's a netinst (or netboot) ISO at ... one second please ... okay, here it is. ...

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by cowlip on 2007-03-20
It looks like you need to do a little bit to get it going, but yes you should be able to:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)
[https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall](https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall)
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

K.Mandla's solution looks great, I wasn't even aware Ubuntu had a net install--good to know

---

### Post by raja on 2007-03-20
If you can PXE boot, it is fairly straightforward to do. I have followed [this]("https://help.ubuntu.com/community/Installation/Netboot") to install Ubuntu on my laptop which does not have an optical drive.

---

