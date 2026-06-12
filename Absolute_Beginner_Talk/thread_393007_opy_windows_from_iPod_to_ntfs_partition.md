---
title: "opy windows from iPod to ntfs partition"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by limelightos on 2007-03-25
i have backed up my windows partition to my iPod but now i need to get it from the 'pod to the partition. i have tried using knoppix to copy it but i don't have permissions. does anyone know of a tool to do this?

---

### Post by halitech on 2007-03-25
what exactly are you trying to do? if you need to move things around and resize partitions, a better option would be the gparted live cd.

---

### Post by limelightos on 2007-03-25
i'm trying to get my windows data from my ipod to the ntfs partition but i can't because i dont have permissions

---

### Post by halitech on 2007-03-25
are you in linux or windows doing the copying to the ntfs partition? if in windows, no idea, if linux, most will not write properly to ntfs and if you don't have it set up as being the owner of the partition, you can't.

---

### Post by cowlip on 2007-03-25
I would load a Ubuntu live cd.

To write to ntfs you need to install ntfs-3g, which should be in the repositories, you probably have to enable the 'universe' repos first.  Then, you should install [ntfs-config]("http://flomertens.free.fr/ntfs-config/") to be able to mount ntfs drives.

---

