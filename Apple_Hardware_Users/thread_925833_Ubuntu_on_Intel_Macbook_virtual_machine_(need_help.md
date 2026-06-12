---
title: "Ubuntu on Intel Macbook virtual machine (need help with graphics)"
date: 2008-09-21
forum: Apple Hardware Users
---

### Post by fjgrf on 2008-09-21
Hi. I'm running Kubuntu on my Macbook (the newest generation) using virtualbox and I have the virtualbox tools on it and stuff, but I cant use any 3d acceleration. I know these Macbooks have an integrated Intel card, but is there a way to take advantage of the graphics card? I can't play any games or use desktop effects etc. Thanks!

---

### Post by cyberdork33 on 2008-09-21
> **fjgrf said:**
> Hi. I'm running Kubuntu on my Macbook (the newest generation) using virtualbox and I have the virtualbox tools on it and stuff, but I cant use any 3d acceleration. I know these Macbooks have an integrated Intel card, but is there a way to take advantage of the graphics card? I can't play any games or use desktop effects etc. Thanks!
It is not your hardware that is the problem, it is the VM. The Virtual Machine's virtual graphics card does not support 3D acceleration. This is true for other VMs too. (when running Linux at least)

---

