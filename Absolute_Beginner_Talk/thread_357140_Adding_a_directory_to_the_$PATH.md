---
title: "Adding a directory to the $PATH"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-09
I'd like to add a directory to the $PATH. I looked at the Ubuntu WIKI but I couldn't really make heads nor tails of it (seems the WIKI is aimed more to developers than users). The WIKI lead me to believe, though, that several files need to be edited but they didn't say which. Is this so?  Anyway, is there an easy way to add to the path? Maybe something along the lines of editing the autoexec.bat in MSDOS.

---

### Post by taurus on 2007-02-09
Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Now, add these two lines to it.

```
PATH=$PATH:**new_path**:**more_new_path**
export PATH
```
Log out and back in again.

---

### Post by Patrick K on 2007-02-09
Yeah, it worked. I don't know why the WIKI didn't just say that. Thanks!

---

