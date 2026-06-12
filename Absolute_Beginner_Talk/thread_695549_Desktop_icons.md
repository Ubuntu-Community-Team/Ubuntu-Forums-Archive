---
title: "Desktop icons"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by timbosity on 2008-02-13
How does one get rid of desktop icons in XFCE. I have found a few threads dealing with desktop icons in ubuntu (gnome) but couldnt figure out anyting for Xubuntu. I just want to have my home folder and a quick launch for terminal on my desktop. At moment all plug and play devices, trash, file system, windows partition and more show up as icons on my desktop. How do I get rid of these guys?

Cheers

---

### Post by joeashcraft on 2008-02-13
I don't use XFCE, but I did find a relevant [helpful page]("http://svn.xfce.org/svn/xfce/xfdesktop/branches/xfce_4_4/README").

In short, you need to **edit** (possibly create) the file **~/.config/xfce4/desktop/xfdesktoprc** and modify (or create) the lines under [file-icons]:
show-home=true
show-trash=false

example:
```
[file-icons]
show-filesystem=false
show-trash=false
show-removable=false
show-home=true
```

---

### Post by timbosity on 2008-02-13
Thanks buddy. That worked a treat. And thanks for the link, i never think of looking at the XFCE pages... should really add them to a bookmark somewhere...
Just have to figure out how to get the terminal there although I suppose putting it up in the toolbar will probably be more useful. 

Cheers

---

