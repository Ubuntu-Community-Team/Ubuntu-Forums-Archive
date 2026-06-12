---
title: "Mass renaming utility for Ubuntu?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by mohapi on 2006-02-04
Is there a utility that will allow me to rename large clumps of files at a time? In WinXP I used THE Rename, which was an exceptionally powerful little tool. I'd like to rename some digital photos, and I'd rather not go through them one-by-one.

---

### Post by bscbrit on 2006-02-04
No, I haven't found a GUI that does the same thing but it is still very easy to achieve from the command line using 'find'.  For example:

find -name 'namenow' -exec mv {} 'newname{}' \;

Try looking at 'man find' on the command line.  Yes, I know that it isn't as convenient but it is a lot more powerful!

Alternatively, if you view your pictures using gThumb, it has a mass-rename capability built in, and I suspect several other graphic packages also have something similar.  But, as you have observed, there is nothing built into Gnome to do the job straight off.

---

### Post by mohapi on 2006-02-04
Excellent. Thanks.

---

### Post by jrib on 2006-02-04
the 'rename' command works :)

(Easy to use if you already know about regex.  If not, then you'll have to learn the basics.)

---

