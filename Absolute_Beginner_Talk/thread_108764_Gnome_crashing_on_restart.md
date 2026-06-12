---
title: "Gnome crashing on restart"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-26
I have been working with my fstab file and after I make a change in gedit, I usually exit out of Gnome by hitting Alt+Ctrl+Backspace.

I login from the full screen terminal and get to my home prompt.  I then type sudo /etc/init.d/gdm restart  to restart Gnome, but my computer always just displays a black screen like the monitor shut off. 

Why does this happen?  Should I be using a different command?

---

### Post by 23meg on 2005-12-26
Try "startx".

---

### Post by Nameless on 2005-12-26
Thank you, I'll give that a try.

---

### Post by Nameless on 2005-12-27
yep, that was it.  I just needed to use "startx"

Thanks!

---

