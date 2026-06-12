---
title: "samba by default?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by LRT on 2007-09-13
i just did a fresh install of ubuntu 7.04 on a machine that is on the same subnet as windows sbs 2003 server. this server acts as a dhcp server (among other things) for other xp machines on the network, including my newly installed ubuntu box. in the gnome desktop, i went to Places -> Network and discovered that i could see all the windows shares on the subnet. i was going to install samba, but since i can already see all the windows shares and apparently have write permissions to them.. i am rethinking having to install samba.

so my question is: is samba installed by default on ubuntu 7.04? i don't think it is, but maybe some of it is? i'm a bit confused. i don't want to start installing samba and mess up any pre-existing configurations. comments are welcome. thanks.

lrt

---

### Post by Bothered on 2007-09-13
The samba server is not installed by default, although the samba client is. Hence in a clean install you can browse the network but cannot share files.

---

### Post by justleen on 2007-09-13
Just leave it as is,  the samba client is installed by default.
Unless, you need to have access from XP to your  Linux machine

Im not on my unbuntu box at the moment, but on fedora it works the same. After i installed Samba through the package managere i got a new menu item under SyStem > Admin, for setting up samba shares...
Piece of cake :)

if you need more contol over samba then what is offered though game, do a search for S.W.A.T.  and samba. google

---

### Post by LRT on 2007-09-13
thanks for replying so quickly. could you tell me which exact samba  tarball(s) is installed by default?

---

### Post by Bothered on 2007-09-13
If you launch synaptic (Administration->Synaptic Package Manager) select "status" from the bottom left buttons and then select "Installed" from the list on the left you can see exactly which packages your system currently has installed. smbclient will be one of those - you can see details about it by selecting it from the package list.

---

### Post by LRT on 2007-09-14
how could i access the windows shares from the command line?

---

