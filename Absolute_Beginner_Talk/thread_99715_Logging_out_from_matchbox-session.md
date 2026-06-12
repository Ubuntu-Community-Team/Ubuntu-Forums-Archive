---
title: "Logging out from matchbox-session"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by ariszlo on 2005-12-06
Here's the content of my /usr/share/xsessions/matchbox.desktop file to log into matchbox-session from GDM:

```
[Desktop Entry]
Name=Matchbox
Exec=matchbox-session
Type=XSession
```

But how do you log out?

---

### Post by ranf on 2005-12-06
It' some months ago that I tried matchbox.
I think it has a command like "matchbox-remote". Run this in a terminal:
```
matchbox-remote --help
```

---

