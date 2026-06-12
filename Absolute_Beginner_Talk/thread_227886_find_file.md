---
title: "find file"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by alainsamoun on 2006-08-02
How do I find a file in the file system? (Other than scanning all the dirs...)

---

### Post by easyease on 2006-08-02
you can do the "sudo whereis (file your looking for)" command from terminal.

---

### Post by tuxinvader on 2006-08-02
Or locate. "locate <filename>"

---

### Post by pistcivet on 2006-08-02
If locate doesn't find the file (if the file was just created):
sudo updatedb
will force an update of the locate database. :)

---

### Post by aysiu on 2006-08-02
You could also go to Places > Find Files/Folders (which is the command *gnome-search-tool*).

---

