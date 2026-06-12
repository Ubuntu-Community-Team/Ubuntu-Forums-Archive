---
title: "[Help] iMac Installation"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by Ax.e on 2008-03-24
I have been using OS X since August 2007 now, and its all working out great, however I miss a bit the days when I used to mess with Linux on my PC, so I recently decided to install Ubuntu on my iMac (*Intel Core 2 Duo, ATi Radeon X1600, 1 GB RAM*). However I encountered two problems:

A) Whenever I load the LiveCD and boot into Ubuntu, Xserver fails - never managed to fix it even by reconfiguration.

B) Installation for iMac feels very under-documented, all of the guides are for MacBooks etc. I have no idea where to start, I'm not risking anything because I don't want to mess up OS X.

Could someone please tell me why is Xserver is failing, and what are the steps that need to be taken to dual-boot between Ubuntu and Mac OS X? *(I am running the latest version of OS X, so I have BootCamp which should be necessary for partitioning*). 

Thanks for your help (:

[RIGHT]- Ax.e[/RIGHT]

---

### Post by cyberdork33 on 2008-03-24
> **Ax.e said:**
> B) Installation for iMac feels very under-documented, all of the guides are for MacBooks etc. I have no idea where to start, I'm not risking anything because I don't want to mess up OS X.yep, I have tried to start a new page, but it is developing slowly.

> **Ax.e said:**
> Could someone please tell me why is Xserver is failing, and what are the steps that need to be taken to dual-boot between Ubuntu and Mac OS X? *(I am running the latest version of OS X, so I have BootCamp which should be necessary for partitioning*).
Mostly because ATI is a PITA.

You "install" process is going to be pretty much the same as any other Mac. partition the drive, then install to the free space. This can be done with disk utility on leopard, with the bootcamp utility, or with the commandline (which is what the other tools I mentioned use under the GUI). You can also try using gparted to resize your OSX partition.

I have pretty much finished the "install" part of the new wiki page, but in your case you may need to use the alt cd since xorg is not working. [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

Please add information if you can.

---

### Post by Ax.e on 2008-03-25
> I have pretty much finished the "install" part of the new wiki page, but in your case you may need to use the alt cd since xorg is not working.

Which alternate install CD should I use? Will [this](http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.iso) work for me?

---

### Post by cyberdork33 on 2008-03-25
> **Ax.e said:**
> Which alternate install CD should I use? Will [this]("http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.iso") work for me?
That is the Gutsy 64bit alt cd. so if that is what you want (as opposed to using Hardy or 32 bit) then yes.

---

### Post by Ax.e on 2008-03-25
I'm gonna go with **ubuntu-7.10-alternate-i386**, I'll update you soon with results.

---

### Post by freddyr0 on 2008-05-26
> **cyberdork33 said:**
> That is the Gutsy 64bit alt cd. so if that is what you want (as opposed to using Hardy or 32 bit) then yes.

Hello cyberdork33, i've been reading a lot of post about how to install ubuntu on an imac, but all of the post i've read are for dual booting. What if i want to get rid completly of mac osx? what installation steps should i take? do i have to make all the steps as regular? or can i just wipe all the hd with the ubuntu partitioner?

Thanks a lot in advance.

Freddy.

---

### Post by cyberdork33 on 2008-05-26
> **freddyr0 said:**
> Hello cyberdork33, i've been reading a lot of post about how to install ubuntu on an imac, but all of the post i've read are for dual booting. What if i want to get rid completly of mac osx? what installation steps should i take? do i have to make all the steps as regular? or can i just wipe all the hd with the ubuntu partitioner?

Thanks a lot in advance.

Freddy.
Just wipe and install, but I would recommend keeping an install of OSX to update firmware and such. You can set rEFIt to boot your Linux install automatically.

Also, from now on, please post questions in the new Apple Users' forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

