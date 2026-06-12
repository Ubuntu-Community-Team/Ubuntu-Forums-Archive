---
title: "Changing Location of Firefox Bookmarks"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-04-24
I want to change where FF stores its bookmarks in Ubuntu (to the same location it does it Windows).

In XP, I would just go change it in the registry, but how would I do it through Ubuntu?

---

### Post by bashologist on 2007-04-24
Maybe you could use a symbolic link?
```
[COLOR="Gray"]# Find your bookmark file like this:[/COLOR]
find ~/.mozilla -name 'bookmarks.html'
[COLOR="Gray"]# Make a symbolic link like this[/COLOR]
ln -s /path/to/real/file /path/to/newlink

```

---

### Post by aysiu on 2007-04-24
> **42Wired said:**
> I want to change where FF stores its bookmarks in Ubuntu (to the same location it does it Windows).

In XP, I would just go change it in the registry, but how would I do it through Ubuntu?
Symlink it? (A symlink is like a shortcut in Windows or an alias in Mac)

---

### Post by orb9220 on 2007-04-24
Or install foxmarks extension for firefox on both xp and ubuntu.

I have it sync my bookmarks on closing firefox and both have same bookmarks.

---

