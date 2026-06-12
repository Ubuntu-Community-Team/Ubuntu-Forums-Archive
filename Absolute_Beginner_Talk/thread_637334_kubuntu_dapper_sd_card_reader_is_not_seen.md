---
title: "kubuntu dapper sd card reader is not seen"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by p-real on 2007-12-10
hello out there. from what i have read the kubuntu dapper version of linux is supposed to automaticaly see my sd card reader do i have to enable something somewhere? any advice?

---

### Post by spiderbatdad on 2007-12-10
I believe you should install pcmcia-cs from synaptic. Then reboot and in a terminal enter:
```
sudo cardctl insert
```

---

### Post by p-real on 2007-12-10
> **spiderbatdad said:**
> I believe you should install pcmcia-cs from synaptic. Then reboot and in a terminal enter:
```
sudo cardctl insert
```
ok im realy new to this so please bear with me i know where i need to put the code in but im not sure how to install pcmcia-cs from synaptic

---

### Post by spiderbatdad on 2007-12-10
the synaptic package manager is your best software source of community maintained software packages. Go to Applications->System->Administration->Synaptic Package Manager. After you have opened synaptic, you will want to enable additional repositories. Choose settings->repositories and check universe and multiverse...haven't seen Dapper for awhile, but i think you'll figure it out. Once you have enabled the repos, you'll need to reload syanptic to see the additional packages, Here's a screenshot that might help:

---

