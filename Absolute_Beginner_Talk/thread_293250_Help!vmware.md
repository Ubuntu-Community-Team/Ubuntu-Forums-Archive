---
title: "Help!vmware"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by kornoholio on 2006-11-04
i just installed VMware-workstation 5.5.1-19175 .... when i loaded the program n tried to power on the machine they asked me to enter a serial number ](*,) any suggestions?

---

### Post by taurus on 2006-11-04
I believe you can run it for 15-day and after 15-day, you need to purchase it!!!  Otherwise, you can always check out qemu...

---

### Post by funrider on 2006-11-04
if all you want to do is to run a VM, you can try vmplayer. If you want to create your own VM, vm server can do it and it is free.

VM workstation requires a serial number since it is not free at all.

---

### Post by gruffy-06 on 2006-11-05
After creating a virtual machine in VMware Workstation, open it in VMware Player. The only things you cannot do are:

> Change any CD/Floppy disk images while running your VM
> Run multiple VMs
> Use multiple snapshots
> Run a team configuration
> Install the propietary VMware Tools package - you cannot access the ISO image in VMware Player

Note that VMPlayer comes with Workstation, so no need to use the separate package.

Or you could try Xen or Qemu.

---

### Post by dmizer on 2006-11-05
you can:
> change any cd/floppy disk images while running your vm
> run multiple vm's
> use multiple snapshots
> install vmware tools
> create new custom machines from scratch

when using vmware server.

vmware server is free of charge, and is several steps faster than quemu or xen.  vmware server will also requre a key, but you can get the key for free by registering.

i've been using it for several months now on my office machine.  haven't had a single issue with it.  and fast too, it always has a machine running while i'm using ubuntu.

---

