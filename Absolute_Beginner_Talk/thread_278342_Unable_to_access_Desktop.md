---
title: "Unable to access Desktop"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-16
Cheers,

I encountered a strange thing suddenly I can access my desktop.  My icons are gone, my folders are gone, I cant create a new item on my desktop.  but the funny thing is that the Desktop folder is still there along with the contents because I can still see it from /username/Desktop.

Any ideas?

---

### Post by Bachstelze on 2006-10-16
Maybe your Desktop permissions got changed somehow, try this :

```
cd && ls -l | grep Desktop
```

and paste the line you get.

---

### Post by delphiguy on 2006-10-16
Ok this is the line I got when executing the code above
drwxr-xr-x 3 delphiguy delphiguy     4096 2006-10-16 19:26 Desktop

Does this makes sense?

---

### Post by delphiguy on 2006-10-16
Ok I dont know what went wrong but I tried to restart my pc again and during boot-up ubuntu check my harddrive and continued booting and when gnome loaded my desktop is back again.

---

### Post by dannyboy79 on 2006-10-16
sometimes gnome loses control of your desktop and you can always make sure that in your window manager settings that the little check box that states, "let gnome control my desktop" is checked. I could be wrong about where that setting is, but I know it something in preferences. like window manager tweaks or window manager settings or something to do with window manager. this may a place to look before you do a restart.

---

