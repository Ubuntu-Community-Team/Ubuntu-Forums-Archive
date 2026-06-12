---
title: "[SOLVED] 91 updates"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-01-21
just installed ubuntu 6.06 and it says there are 91 updates should i really install all them at once

---

### Post by Bachstelze on 2007-01-21
Those are mostly security updates so you should indeed install them ASAP, especially if the computer is connected to the Internet.

---

### Post by mand0 on 2007-01-21
Some updates may break certain programs/drivers so be careful.  Case in point, the Beryl updates earlier gave many people problems but were quickly fixed with a new update.

---

### Post by rusty4r on 2007-01-21
thanks i will right now

---

### Post by aysiu on 2007-01-21
> **mand0 said:**
> Some updates may break certain programs/drivers so be careful.  Case in point, the Beryl updates earlier gave many people problems but were quickly fixed with a new update.
Ah, but Beryl is in beta. If you're doing a fresh install, the chance of breakage from updates is almost 0%.

---

### Post by xael on 2007-01-21
Yes, my humble advice is also to install those updates right away. They are  quite probably security updates.

---

### Post by halitech on 2007-01-21
I just installed Xubuntu 6.06 on my nephews machine and it didn't give any notice of any updates. Shouldn't it give the same warning?

---

### Post by aysiu on 2007-01-21
> **halitech said:**
> I just installed Xubuntu 6.06 on my nephews machine and it didn't give any notice of any updates. Shouldn't it give the same warning?
Yes, it should if you have a working internet connection on that computer.

Run the command ```
sudo aptitude update && sudo aptitude dist-upgrade
``` on your nephew's machine. If there are updates, that command will install them. Otherwise, it'll let you know your system is up-to-date by not installing/updating anything.

---

### Post by halitech on 2007-01-21
Net is definately working, I've got it running automatix to grab the plugins and whatnot (just being lazy tonight) so will run that once it's done. 

Thanks

---

### Post by rusty4r on 2007-01-21
got them all done thanks again guys

---

### Post by LeslieL on 2007-01-21
Ooops = didn't mean to reply. You have good advice already

---

