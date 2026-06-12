---
title: "Some vmware player questions"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-06-22
1) on vmware's site, there is no deb available for vmware player, it's just a rpm. Does the deb obtained using alien work?

2) where can I find a MS-DOS (recent version) vmware image?

thank you

---

### Post by Miguel on 2006-06-22
Regarding 1) "Alienated" debs do not always work. However, in my experience, they usually do. As vmware is a propietary product, it will probably use static linking, and thus it will most probably work. 

You don't lose anything installing the deb (as long as you trust the vmware company, never ever install a deb from someone you don't trust). You can easilly uninstall it later using either Synaptic, Adept or apt-get.

2) No idea, sorry

---

### Post by az on 2006-06-22
[QUOTE=zugu]1) on vmware's site, there is no deb available for vmware player, it's just a rpm. Does the deb obtained using alien work?

2) where can I find a MS-DOS (recent version) vmware image?

thank you[/QUOTE]
Enable multiverse and install vmware-player from the Ubuntu repositories.  You can't expect one company to provide packages for every single distro's kernel.  Everything is already built for you in the multiverse repo.

---

