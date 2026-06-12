---
title: "where to download software"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-02
where is the best place to find and download linux software, i remember one site that i found had recomendations for software compared to windows software

---

### Post by oilchangeguy on 2007-05-02
what kind of software are you looking for?
this might help:
[http://www.linuxeq.com/](http://www.linuxeq.com/)
see also, applications, add/remove
automatix, [www.getautomatix.com](www.getautomatix.com)
system, admin, synaptic package manager

---

### Post by silent1643 on 2007-05-02
well after my previous partition problems (check previous topic i posted), i need to resize the ubuntu partition to its max size, i installed ubuntu (with partition errors) and lost my xp install, so now my previous xp partition is unallocated, so i need to format it and i guess resize my current ubuntu :D

---

### Post by Drooling Iguana on 2007-05-02
Gparted is probably your best bet. It can be installed from the regualr Add/Remove interface.

---

### Post by silent1643 on 2007-05-02
> **Drooling Iguana said:**
> Gparted is probably your best bet. It can be installed from the regualr Add/Remove interface.

right thats what i need, but how do i resize my current partition (the one with ubuntu on it) so that it is using the max space, right now its locked apparently

---

### Post by Drooling Iguana on 2007-05-03
Sorry, can't help you there. I've never actually resized a partition without reformatting. Hopefully someone else reading this thread will have more experience in that area.

---

### Post by igknighted on 2007-05-03
You can't resize a partition while using it (you need to boot from the liveCD).  Also, you can't resize forward on a disk (so if your XP partition was before linux you can't take that space over).  However, you can make a new partition in that space while in Ubuntu and then mount that partition (preferably in your home folder so you can use it as extra space).  Failing that, you could use it to try other linux distros too, after all there are thousands to choose from.

---

### Post by silent1643 on 2007-05-03
so i can't boot from live cd, run gparted, format the unallocated space, &  resize the ubuntu partition so it uses the un allocated space? I know i put my ubuntu partition towards the end not in front.

---

