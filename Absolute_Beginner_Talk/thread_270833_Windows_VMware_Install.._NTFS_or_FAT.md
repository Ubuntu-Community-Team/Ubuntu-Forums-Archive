---
title: "Windows VMware Install.. NTFS or FAT?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by FreakinSyco on 2006-10-03
Like the title asks.. Im installing an XPpro install on VM Server and want to know if I should setup the VM Disk as NTFS or FAT or if it even matters.

---

### Post by drr422 on 2006-10-03
I just installed XP home yesterday on VMWare and i selected FAT,  It works for me, snd pretty good too, I have it set up so that i can just access those programs that I need to run in windows, so that I can run everything else in Ubuntu. 

Dustin

---

### Post by comppsyco on 2006-10-03
I would go for NTFS, because you won't be able to access it from Ubuntu anyway, and there's no file size limit.

---

### Post by FreakinSyco on 2006-10-03
I went with NTFS just because.. Works fine.

---

### Post by hyper_ch on 2006-10-04
and if you need to share files accross you can use samba for it :)

---

### Post by jaboua on 2006-10-04
> **comppsyco said:**
> I would go for NTFS, because you won't be able to access it from Ubuntu anyway, and there's no file size limit.
Actually, you should be able to mount it as normal partition if you mount it as a loop device

---

