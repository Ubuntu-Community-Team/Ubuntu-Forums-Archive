---
title: "Hdd do not boot after install"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Strumphuletsz on 2007-02-16
Hi! I have a little problem. I want to install Ubuntu on my hdd instead of running from CD. Now i'm on CD, connected to the internet, but i want "maximum speed" and to extend my CD-ROM life. So. I installed ubuntu on my secondary master hdd by using partitioning program and deleting the logical drive (so having unused space on my hdd), stepping back and specifying to Ubuntu to make the install automatically. It started, ok, installing, ok, restarting, ok, but booting again from hdd, not from cd-rom, no. I thing that the installation program didn't wrote the MBR of hdd (it seems to be unmodified). Do U know how can i write it manually or using a program? Thx a lot, guys!

---

### Post by shareMenaPeace on 2007-02-16
When you run the live cd can you start gparted from 
system -> administration -> gnome partititon manager - make a screenshot of your drieves and atache it?

---

### Post by Strumphuletsz on 2007-02-16
> **shareMenaPeace said:**
> When you run the live cd can you start gparted from 
system -> administration -> gnome partititon manager - make a screenshot of your drieves and atache it?

In the meantime I resized the big partition trying to make a bigger swap file of 500 Mb. I restarted and the same message from MBR... And now this is how my hdd looks...

---

### Post by shareMenaPeace on 2007-02-16
As your hd is very small i suggest you might use the alternate cd which i guess doesnt installs so much stuff and i think minimm recommend disc space is 5gb.(You get 10-40gb hdd very cheap in 2nd hand business) But you can try ofc.

You have unallocated space and 2 swap partitions, i suggest you reinstall and merge all existing partitions to somethink like

```
hdc1 4gb ext3
hdc2 500mb swap
```

---

