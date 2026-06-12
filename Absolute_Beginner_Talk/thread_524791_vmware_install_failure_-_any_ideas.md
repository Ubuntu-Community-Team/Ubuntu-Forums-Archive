---
title: "vmware install failure - any ideas?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by bren on 2007-08-13
hi all

i followed this guide

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html) 

to install vmware server

unforunately it seems to have failed   Here is the last few lines of the install process

```
The subnet 192.168.21.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.21.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Generating SSL Server Certificate

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.



Setting up vmware-tools-kernel-modules-2.6.20-15 (2.6.20.5-15.20) ...

Setting up vmware-tools-kernel-modules (2.6.20.15.14) ...
```

Does anyone know why the VMWare services failed above?
I tried running VMWare Server Console and creating a new virtual machine for XP home anyway but it gave the following message when i tried to power it on 
```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

---

### Post by ddrichardson on 2007-08-24
Wht is the output of ```
lsmod | grep vmnet
```?

---

