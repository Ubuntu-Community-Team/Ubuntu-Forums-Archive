---
title: "Map network drive?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-22
Okay so if I was on windows xp, I'd right click my computer click map network drive, click browse and all my shared folders would be there. I could go into my documents select a folder click share folder and share it, now that I'm on Linux Ubuntu how do I share a folder from this computer, *Linux* to my windows XP computer? I use to be able to do it when I ran XP on this computer but now I am running linux, thanks.

---

### Post by spiderbatdad on 2008-02-22
There's a little more work involved to share files between a windows computer and a separate Linux computer. Have a look into samba, though you can get away with just a smbfs plugin. Here's a guide as an introduction. It really isn't too hard once you get into it. [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by zerhacke on 2008-02-22
You don't need samba to mount a cifs share.  smbfs is enough.

If you want to share from the linux computer to the windows computer you need samba, but since you said map network drive (Windows talk for mount a cifs share) I'm assuming you want the Linux box to see the Windows shares.

---

### Post by spiderbatdad on 2008-02-22
:popcorn:

---

