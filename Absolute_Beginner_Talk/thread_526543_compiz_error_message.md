---
title: "compiz error message"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by whiffy badger on 2007-08-15
Trying to get compiz-fusion working without any joy.

When I type "compiz --replace" in to a command line, I get this error message:

newton@Computer3:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

(gtk-window-decorator:6355): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6355): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6355): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6355): Wnck-WARNING **: Unhandled action type (nil)


Could anyone tell me please how to get compiz working - thanks!

---

### Post by st33med on 2007-08-15
This is supposed to be in the Desktop effects forum... Ah, well, I'll help.

Try this:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
```

Did that work?

---

### Post by whiffy badger on 2007-08-15
**I take your point that I am posting in the wrong forum for which I apologise.  No It hasn't resolved it ... I now get:**

newton@Computer3:~$  LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
[1] 7520
newton@Computer3:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7548): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

**Thanks anyway!  I will repost in the correct forum.**

---

### Post by sailor2001 on 2007-08-15
I belive you're supposed to post compiz --replace in alt/f2 not in the terminal. Interminal I believe it is compiz --replace emerald &

---

### Post by dougfractal on 2007-08-15
can you post this
> lspci -nn
cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf

probably best to post as file attachments.

---

### Post by st33med on 2007-08-15
He said he moved the post to Desktop Effects.

---

