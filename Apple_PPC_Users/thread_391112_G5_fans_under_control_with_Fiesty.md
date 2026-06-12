---
title: "G5 fans under control with Fiesty"
date: 2007-03-22
forum: Apple PPC Users
---

### Post by stmiller on 2007-03-22
Just tested the Feisty herd-5 live-desktop CD on my G5 and the fans work as expected.

My machine:
Powermac G5 dual CPU 2Ghz
(Powermac 7,3)
Radeon 9600


(Had to edit the xorg.conf file to say
Option          "UseFBDev"              "false"
to get X to start though on this live CD.)


Here is the infamous bug report:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34723](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34723)

---

### Post by stmiller on 2007-03-22
Okay I installed the Fiesty dev release on my Powermac G5 and all is well. The installer quit at the very end before creating the bootloader (yaboot) and configuring it. So if you are going to give it a shot, be prepared to create your own yaboot.conf and write that to the boot partition.

Mac keyboard shortcuts work (Volume, eject CD, brightness).

Openoffice 2.2, Firefox 2.0.0.2, Gaim 2.something, 2.6.20 kernel. All pretty up-to-date stuff.

VLC, digikam, and lots of other goodies available right away in the add/remove software thingy.

Pretty nice.

---

