---
title: "rsync on logout"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by pzs on 2008-02-29
I would like to synchronise my filespace to an external server when I switch off my machine. My sychronisation script uses rsync. Two questions:

1. Where to I put the script to make it execute on shutdown? After reading some other forum posts, I I tried /etc/gdm/PostSession/Default but it doesn't seem to work.

2. How do I stop the script from being interrupted if it doesn't finish by the time a killall gets sent?

Thanks,

Peter

---

### Post by Oldsoldier2003 on 2008-02-29
> **pzs said:**
> I would like to synchronise my filespace to an external server when I switch off my machine. My sychronisation script uses rsync. Two questions:

1. Where to I put the script to make it execute on shutdown? After reading some other forum posts, I I tried /etc/gdm/PostSession/Default but it doesn't seem to work.

2. How do I stop the script from being interrupted if it doesn't finish by the time a killall gets sent?

Thanks,

Peter
why not write a script that rysncs than logs you out/does a shutdown?

---

### Post by pzs on 2008-03-03
I could do, but it's a bit of a hack. Surely there's a standard way of executing things at shutdown time...

Anybody?

Peter

---

