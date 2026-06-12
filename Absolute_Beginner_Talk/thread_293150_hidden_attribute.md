---
title: "hidden attribute"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by manfredell on 2006-11-04
How do I change the hidden attribute of a directory (or file)?

---

### Post by blendmaster on 2006-11-04
Open up a file, and hit ctrl-H, or click View >> Show Hidden Files, if that's what you meant.

---

### Post by manfredell on 2006-11-04
This is how I can SHOW hidden files or directories. What I meant is how to change them to be NOT hidden, i.e. to show when the show hidden files is off.

---

### Post by taurus on 2006-11-04
> **manfredell said:**
> This is how I can SHOW hidden files or directories. What I meant is how to change them to be NOT hidden, i.e. to show when the show hidden files is off.
Perhaps you mean permissions!!!

---

### Post by manfredell on 2006-11-04
I did not mean permissions.
But I've just found out. I just have to rename the directory from .xxxx to xxxx and it shows.

---

### Post by taurus on 2006-11-04
Don't have to rename anything.  In fact, there are some certain directories that need to have a . in front:  .gnome2, .gkrellm, .gdeskcal, .gdesklets, .adesklets, .xmms, .mplayer, .bashrc, .bash_profile, etc. So, open a terminal, Applications -> Accessories -> Terminal, and type

```
ls -la
```
;)

---

