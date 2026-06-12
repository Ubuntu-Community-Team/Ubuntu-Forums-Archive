---
title: "Question about sharing files between machines"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-06-19
What is the best way to go about setting up a folder on one linux machine that another linux machine on the same network can access and move files to, but still be secure?

---

### Post by lixy on 2007-06-19
> **Jhorra said:**
> What is the best way to go about setting up a folder on one linux machine that another linux machine on the same network can access and move files to, but still be secure?

Try NFS or Samba.

---

### Post by starcraft.man on 2007-06-19
[The answer to all Samba sharing questions.]("https://help.ubuntu.com/community/SettingUpSamba")

I believe that is the easiest question tonight :D.

---

### Post by Jhorra on 2007-06-20
What if I'm not trying to get to the folders from a Windows machine, but another linux machine?  Everything on that page was geared towards Windows.

---

### Post by Songwind on 2007-06-20
SAMBA is just a file sharing protocol.  it works just fine from one Linux box to another.

---

