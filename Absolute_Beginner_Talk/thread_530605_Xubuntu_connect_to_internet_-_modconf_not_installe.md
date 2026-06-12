---
title: "Xubuntu connect to internet - modconf not installed"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by ptirapeo on 2007-08-20
Hello.

New to Linux.  Installed Xubuntu perfectly fine.
Tried plugging ethernet cable to connect to internet, but no luck.

I tried
~$ sudo pppoeconf          but asked to try modconf - didn't work.

then I tried
~$ sudo apt-get install modconf          but said: E: couldn't find package modconf

Not sure how to arrive at my Device Manager either to know whether it's finding my network card.  I tried ~$ lspci, but I do not know how to tell where to see the network card.

I looked on this forum for info, but only noticed to find the Device Manager on Ubuntu, but not Xubuntu.

Can anyone help?

---

### Post by gn2 on 2007-08-20
Applications>System>Network 

If your network adapter is detected it will be shown in there.

---

### Post by ptirapeo on 2007-08-20
Thanks for responding.

I actually cannot see it on the Network, all I see is my modem, which states "this network interface is not configured".
However, I typed "lspci" on the command prompt and I see this:
Host bridge: intel...
PCI bridge: intel...
ISA bridge: intel...
IDE interface: intel...
USB Controller: intel...
CardBus bridge: Texas Instruments PCI1410...
Communication controller: conexant HSF 56k data/fax modem
Multimedia audio controller: ess...
vga compatible controller: ATI ...

I'm not sure if one of these is the ethernet card, can you tell?

---

