---
title: "Backup the updates"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by sapphire56 on 2006-08-11
I was wondering if it is possible to backup all the updates for ubuntu so i dont have to download them all again

---

### Post by Dr. Nick on 2006-08-11
actually a maintaince update for dapper was released today which includes all updates to this point.

I think their is a way to backup them up though, not sure exactly how though, the debs should still be in /var/cache/apt

---

### Post by ubunlilluz on 2006-08-11
how can i restore them? i don't think that ubuntu will see a backed up directory like it was a repository. i scare i'll have to install with dpkg -i
one by one...

---

### Post by Jagot on 2006-08-11
> **ubunlilluz said:**
> i scare i'll have to install with dpkg -i
one by one...

```
sudo dpkg -i *.deb
```

---

### Post by ubunlilluz on 2006-08-12
and the dipendences? If i'll run dpkg -i *.deb, will all files installed in the right order and them will be respected?

---

### Post by Dr. Nick on 2006-08-12
dpkg -i *.deb will install all packages in the folder, not sure if it will handle dependencies, most updates dont have many dependencies that are not already installed, or inccluded in the updates. I dont think

---

