---
title: "gconf-editor"
date: 2011-04-07
forum: Any Other OS
---

### Post by galacticaboy on 2011-04-07
I went into gconf-editor and enabled access to my desktop. I use Elementary OS and it is disabled by default, I could not put anything on my desktop or right click, so I enabled that, now I can, but it is an ugly grey background, and it will not let me change the background, it stays grey. How can I fix this?

---

### Post by howefield on 2011-04-07
Thread moved to "*Other OS/Distro Talk*"

---

### Post by galacticaboy on 2011-04-07
Anyone?

---

### Post by Perfect Storm on 2011-04-09
Which options did you enable?

<alt>+<F2>
```
gconf-editor
```

Apps ---> Nautilus ---> Preferences
"Show Desktop" [x]
"Desktop_is_home_dir" [ ]


To enable configurations of Panels:

Apps --> Panel ---> Global
"disable_lock_screen" [ ]

---

