---
title: "Creating a Shortcut to folders in home"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-11-03
I have a shared fat32 partition (oh for the day I no longer need to share!), and I want to create shortcuts which link to various useful folders (i.e. My Music, My Pictures etc.) to make saving ad finding things a bit easier.

How would I go about this?

---

### Post by bodhi.zazen on 2006-11-03
> **happy-and-lost said:**
> I have a shared fat32 partition (oh for the day I no longer need to share!), and I want to create shortcuts which link to various useful folders (i.e. My Music, My Pictures etc.) to make saving ad finding things a bit easier.

How would I go about this?

I would use the CLI (terminal)

```
cd
ln -s /full_path/to/My\ Music Music
ln -s /full_path/to/My\ Pictures Pictures
...
```

_Note_: Watch the "\" to "escape" the space in "My Music" and "My Pictures" (Linux does not like the space in the path) and the space between Music and Music (and Pictures Pictures).

---

### Post by happy-and-lost on 2006-11-03
Worked a treat thanks :D

---

### Post by kerry_s on 2006-11-03
You can also use 2 windows and drag & drop.

---

### Post by CatKiller on 2006-11-03
> **kerry_s said:**
> You can also use 2 windows and drag & drop.

My favourite is the middle-click & drop. But then my favourite in Windows was the right-click and drop, so it's hardly surprising.

---

