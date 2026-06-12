---
title: "[SOLVED] Changing Permissions"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-07-26
What is the command so I can bring up my file browers and browse through under root to change some permissions that I normally can't as my regular user?? Thanks!

---

### Post by aktiwers on 2007-07-26
```
gksudo nautilus
```

---

### Post by skymera on 2007-07-26
this will add the option to applications menu

first
 ```
 gksudo gedit /usr/share/applications/Nautilus-root.desktop 
```

in that file add:

```
 [Desktop Entry]
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;

```

---

### Post by charlier653 on 2007-07-26
on this subject.......

why am I getting this response?

(gedit:22139): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Tumpster on 2007-07-26
Awesome, thank you folks!! I greatly appreciate it!

---

### Post by aysiu on 2007-07-27
> **charlier653 said:**
> on this subject.......

why am I getting this response?

(gedit:22139): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
It's a bug. Ignore it.

---

### Post by charlier653 on 2007-07-28
thanks Aysiu!!

I didn't know if it was something important or not.

C

---

