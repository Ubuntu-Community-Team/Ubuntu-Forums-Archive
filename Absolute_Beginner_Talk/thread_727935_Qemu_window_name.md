---
title: "Qemu window name"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by nousefreak on 2008-03-18
Hi,

I'm using qemu for simulating a proff network, but to make it more handy, i would like to use the "-name" function of witch I read on [http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC10]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC10").
But when I add the option to my start rule, it doesn't start and gives me

```
qemu: invalid option -- '-name'
```

rule I run: 

```
qemu -hda /home/nousefreak/.VirtualMachines/hda.img -m 128 -net nic,vlan=2,macaddr=52.54.00.12.34.02 -net socket,vlan=2,connect=localhost:1234 -name Xubuntu
```

I am running Qemu 0.9.0-2 on my Ubuntu 7.10 

Can someone please tell me why this is not working?

---

