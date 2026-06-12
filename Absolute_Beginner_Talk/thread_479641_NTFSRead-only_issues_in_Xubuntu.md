---
title: "NTFS/Read-only issues in Xubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by haaskaa on 2007-06-20
My brand new external hard-drive that I have formatted as ntfs works perfectly when I plug it into my Archlinux box. My Xubuntu (Feisty Fawn) laptop on the other hand insists that it is Read-Only! 

I tried with ntfs-config but with no luck.

Does anyone have an idea why it is Read-only in Xubuntu but read/write in Archlinux ?

---

### Post by notbitmonk on 2007-06-20
If I read correctly, [K/X/Ed]Ubuntu will only provide read-only access to an NTFS drive.  You could install the ntfs-"something" (I don't remember the exact name but its in one of the post for the past couple of days) to enable read/write access.

---

### Post by Soybean on 2007-06-20
I believe you just have to install the "ntfs-3g" package, although it's been a while since I've done it so I'm not 100% sure.

To answer your question literally, the reason for the difference is that the Ubuntu devs don't think ntfs-3g is stable enough to be installed by default. There's still some danger (though I understand it to be quite small) that writing to an NTFS partition from Linux will damage the file system.

---

### Post by haaskaa on 2007-06-20
> I believe you just have to install the "ntfs-3g" package,

I had installed ntfs-3g and also the gui thing (ntfs-config I believe). But it needed a restart (duh!..) also apparently and now it works perfectly!  :)

Cheers!

---

