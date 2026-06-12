---
title: "terrible (wireless) network performance in feisty"
date: 2007-04-18
forum: Apple Intel Users
---

### Post by vh1 on 2007-04-18
it started happening using either ndiswrapper or madwifi on a C2D macbook a couple of updates ago.

all my media is stored on another computer on my network, and I started noticing that videos would play fine for a few seconds, and then would get incredibly choppy. browsing the computer is unresponsive and causes hangups in konqueror. and when I copy files from it, it only goes at around 100KB/s

the files are shared over NFS so performance should be the same in OSX and ubuntu, but in OSX it's much, much quicker.

what's even stranger is that my internet connection is 1.5mb/s, so I download at ~160KB/s, which is faster than files are transferring between the two computers

---

### Post by ronocdh on 2007-04-21
I don't believe it's possible to use madwifi drivers with a C2D. Am I mistaken here? I thought we C2Ders were forced to use ndiswrapper, because the Atheros chipset isn't well supported yet. Anyway, if that's the case, please post back with the troubles you've had setting up your wireless via ndiswrapper/madwifi.

Also, is this on a fresh install of Feisty?

---

### Post by Chrisj303 on 2007-04-21
> **ronocdh said:**
> I don't believe it's possible to use madwifi drivers with a C2D. Am I mistaken here? I thought we C2Ders were forced to use ndiswrapper, because the Atheros chipset isn't well supported yet. Anyway, if that's the case, please post back with the troubles you've had setting up your wireless via ndiswrapper/madwifi.

Also, is this on a fresh install of Feisty?

I use mad wifi on my macbook c2d - but it's pretty useless at the moment as it dosen't seem to handle any form of encryption.

I use it in conjunction with network manager, and picks up networks fine. The signal dosen't appear do be as strong as it is with OSX, but it's there. 


303

---

### Post by muchmusic on 2007-04-21
the madwifi in feisty doesn't work out of the box though

---

