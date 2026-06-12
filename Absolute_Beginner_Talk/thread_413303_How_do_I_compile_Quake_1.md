---
title: "How do I compile Quake 1?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2007-04-19
Ok so I downloaded Quake 1 source from [QuakeForge]("http://www.quakeforge.net/files.php") (it's the first tar.gz file on that page, not tar.gz2) and it tells me I have to compile it myself... so wonderful Ubuntu Community helpers, how do I do that? :biggrin:

---

### Post by eentonig on 2007-04-19
Why didn't you install from the repositories?

That's one of the greatest features of this distribution. You don't have to look and download software from several websites and start fiddling with dependencies and compiling.

---

### Post by Narcoleptic_Insomniac on 2007-04-19
> **eentonig said:**
> Why didn't you install from the repositories?

That's one of the greatest features of this distribution. You don't have to look and download software from several websites and start fiddling with dependencies and compiling.

Lol I was thinking of that but I wasn't sure if such an old game would have a repository. Since it does, whats it called? Could it really be as simple as sudo apt-get install quake1? I doubt it.

---

### Post by ohioboy757 on 2007-04-19
I think it is quake2 acutally

```
sudo aptitude install quake2
```

---

### Post by eentonig on 2007-04-19
You can always look for it.

Did you open the multiverse and universe repositories?

If so.

> sudo apt-cache search <package_name>

PS. Software doesn't get it's own repositorie. Rather, see the repositories as huge cabinets that get filled with different kind of software. So if the cabinet mainainer decides to put the software in one of the free drawers, it's available.

---

