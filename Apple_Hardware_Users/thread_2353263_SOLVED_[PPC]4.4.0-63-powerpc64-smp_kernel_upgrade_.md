---
title: "SOLVED [PPC]4.4.0-63-powerpc64-smp kernel upgrade kills network"
date: 2017-02-20
forum: Apple Hardware Users
---

### Post by kaynemo2 on 2017-02-20
Tried to upgrade kernel via apt-get and it killed the network (Ethernet), no matter what I do it will not come up, looks like the kernel doesn't load the module. The driver for eth card is r8169. Booted back to previous kernel, and it runs just fine. Any ideas ?

Well there is a solution - 

[COLOR=#333333][FONT=monospace]We've been testing the problem on irc channel. It turns out that the new kernel assigns new names to the network interfaces i.e. the original name (in kernel 62) was enP3168p5s3 and the new kernel assigned the same card and the same interface a new name - enP64624p5s3, therefore - no network obviously, as the /network/interfaces file contained old names. After submitting new names to the config file, the network is up and stable.[/FONT][/COLOR]

---

