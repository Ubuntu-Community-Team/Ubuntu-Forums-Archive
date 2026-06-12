---
title: "What To Back Up And How?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by iancvt55 on 2008-02-19
Hi

Happily getting stuck into Ubuntu and now a month or so on realise I must need to back some files up as there must be config files that are now nothing like what a clean install would look like.

So any advice on what and how to backup would help.

Thanks

Ian

---

### Post by njparton on 2008-02-19
Did you create a seperate /home partition?

---

### Post by herbster on 2008-02-19
Yeah, paste the output of:

```
df -h
```

---

### Post by iancvt55 on 2008-02-19
Pardon my ignorance but I just followed the defaults from the install CD. I do have something called /home/ian but I guess that may just be a folder?

---

### Post by jken146 on 2008-02-19
/home contains all the files belonging to each user (except root, but that doesn't matter).  If ian is the only user, all you have to do is make a copy of home/ian and that will be fine as your backup.  If you reinstall Ubuntu, then copy the backup to its original place, you will have all your files and settings back, but not your programs.

---

### Post by njparton on 2008-02-19
It's best to create /home as a separate partition that way it won't get deleted when you re-install etc.

---

