---
title: "Saving editing files from terminal"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by kdhar on 2006-12-29
Topic says it all. I was editing my "/etc/X11/xorg.conf" file in order to get full function of my Logitech G5. I used and edited it thru Terminal and I completely forgot how to save the file and exit edit mode, any suggestions? reason why I do it this way is because it is the easiest way I find editing files as root(super admin)

---

### Post by ajgreeny on 2006-12-29
I think it depends on what utility you used to do the edit.  If it was nano, I seem to remember it's Ctrl+X, but you need to look at the manual first, (man nano [or whatever utility used]).

---

### Post by meng on 2006-12-29
If it's vim/vi, then you press
[esc]:wq

---

### Post by tommytom on 2006-12-29
> If it was nano, I seem to remember it's Ctrl+X

 It is CTRL+X in nano it says at the bottom of the screen along with the other options.

---

### Post by steve.horsley on 2006-12-29
You may find **gksudo nautlius** easier to get along with. This launches a root file manager, and of course anything you open with that is then running with root privs, including the editor.

---

