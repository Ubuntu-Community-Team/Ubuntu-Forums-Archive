---
title: "no pwd to shutown ?!"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by gian on 2006-10-23
Hi All,

I was surprised to see that you do not need a password to switch off the pc.. everybody can just do it...

I now there might be a way to twist it, but should this be the default setup ?

cheers,
-GianLuca

---

### Post by Aberrix on 2006-10-23
you should have to do a 'sudo shutdown'... you do not?

---

### Post by CatKiller on 2006-10-23
Not if you use the GUI. Don't know any more than that, though.

---

### Post by Bachstelze on 2006-10-23
You can easily tweak it from inside the GDM/KDM setup screen.

---

### Post by Lord Illidan on 2006-10-23
> **HymnToLife said:**
> You can easily tweak it from inside the GDM/KDM setup screen.

give better instructions. Even i don't know how to do it.

---

### Post by Bachstelze on 2006-10-23
I don't remeber exactly how to do it with GDM (GNOME), run

```
gksudo gdmsetup
```

it should be somewhere in there.

With KDM, it's in the Control Panel > Login Manager > "Shutdown" tab (at least on the Fedora box I'm on right now, don't remeber exactly about Ubuntu but you get the idea :)

---

