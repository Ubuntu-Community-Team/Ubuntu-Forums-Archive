---
title: "[SOLVED] Why the dot in home directory filename listings?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-08-07
In my home directory, many of the subdirectories are named with a dot preceding the filename, as in ".azureus".  What is the significance?  

I noticed that when the list sorts, the dot filenames do not sort to the top of the list as one would expect if the sort were alphabetical.  Why not?

---

### Post by Dr Small on 2007-08-07
The dot means the folder is hidden.
About the alphabetical ordering, I have no clue...

---

### Post by deanjm1963 on 2007-08-07
the dot before a file name or directory/folder means it's "hidden". if you're using gnome just hit ctrl+h or show hiddren files if you're using kubuntu. it will show you all your hidden files.

---

### Post by milosz.galazka on 2007-08-07
If you were thinking about console...
Try ```
ls -av
``` where *a* means all and *v* is for sorting

---

### Post by bettyhills on 2007-08-07
Thank you, all!

---

### Post by aysiu on 2007-08-07
The dot technically means it's hidden.

But the significance of the hidden files is that they're user settings. For example, /home/*username*/.azureus contains *username*'s preferences for Azureus.

Likewise, /home/*username*/.mozilla contains *username*'s Firefox bookmarks, history, extensions, and themes.

---

### Post by Rocket2DMn on 2007-08-07
I sorta wish they had a subdirectory in the home folder where all the configs are kept, it makes the home folder pretty cluttered the way it is.  Something like /home/username/.configs/.whatever would be nice, but I guess that's not the custom.

---

