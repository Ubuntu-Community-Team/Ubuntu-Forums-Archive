---
title: "Can I mount a networked NTFS drive for all to read/write?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2007-03-31
Hi all,

Two machines; one edgy, and one xp.

There are shared folders on the XP machine, that I can see on the edgy box by browsing with Nautilus.

Is it possible to mount those folders locally to the edgy box, and then have full read/write access? I have the ntfs-3g package installed.

I cant get my head around how the fstab entry would look.

thanks
John

---

### Post by HellSpawn on 2007-03-31
In this case, you don't need any NTFS compatibility, just a Samba client.

I think you can include this FS in your fstab as CIFS Filesystem : [http://www.samba.org/cifs/](http://www.samba.org/cifs/)

Hope this helps

---

