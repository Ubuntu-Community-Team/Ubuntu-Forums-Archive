---
title: "Giving normal user full access to the shared folder in VMWare fusion"
date: 2009-08-05
forum: Apple Hardware Users
---

### Post by newgalois on 2009-08-05
Hi,

I am running Ubuntu 9.04 on VMWare Fusion (2.05) on my Late 2008 MacBook (Leopard 10.5). I created a shared folder to allow Ubuntu to access my OSX's home. 

As a normal user, I can read the shared folder, but I couldn't write to it. Perhaps the reason is that the folder is mounted by root rather than me. I try to change the permission (chmod) of the folder to allow me to write, but that doesn't help. I verified that root has both read and write access to the folder. 

This happened before when I tried to access the Windows partition on my (previous) PC running Ubuntu. Changing the property of the mount point fixed it, but I don't remember which file to change.

Thanks!

---

### Post by newgalois on 2009-08-06
No one answered me, so I have to figured it out by myself. The trick is to edit the /etc/fstab file. But I have to understand it first. Will report the result once done.

It seems like no one use Ubuntu on Virtual machine? I think it is a nice way: you have the power of Linux and the drivers of Mac. We can't help the hardware manufacturers not wanting to provide Linux drivers.

---

