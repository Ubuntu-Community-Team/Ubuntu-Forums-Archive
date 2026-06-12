---
title: "Renaming files using shell commands."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by renaudb on 2007-12-16
Hi,

I have several files in a directories (and their sub-directories) that I would like to rename, ie, replacing  space characters by "_", accented characters like "é" by "e", etc. I believe there would be a way to do this with shell scripting, but I have no idea how and no experience in that domain. I started to read tutorials on shell scripts, but this is quite a large subject so I was wondering if someone could put me on the right track.

If someone would like to suggest a good batch renamer program, I am open to that solution too. I am running Ubuntu 7.04.

Thanks for your help,
Renaud B.

---

### Post by aktiwers on 2007-12-16
Maybe Krename can help you, in terminal type:
```
sudo apt-get install krename
```
When done, open by typing
```
krename
```

Here is a guide:
[http://linux.about.com/od/KRename/a/KRename2n3.htm](http://linux.about.com/od/KRename/a/KRename2n3.htm)

I thought section 3 looked interesting.

---

### Post by scizzo on 2007-12-16
Suggestion is to use **rename** to change multiple files.

Example:

# rename "s/ *//g" *.bak

Will remove blank spaces for all files that ends with .bak

The reg expressions are perl based.

---

