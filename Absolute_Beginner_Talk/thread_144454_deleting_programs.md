---
title: "deleting programs"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-03-14
hey I have a question about deleting programs I have installed from .debs.  If I want to "uninstall" it should I just delete the folder where the files are installed?   Or is there a command simliar to 

apt-get remove "file"  haha I guess that wouldn't make sense.

I am confused.

---

### Post by Brunellus on 2006-03-14
actually you are correct.

apt-get remove PACKAGENAME

that'll do it.

---

### Post by inovermyheadd on 2006-03-14
oh right....I apologize...I meant deleting files I installed from .bins and .runs

---

### Post by Brunellus on 2006-03-14
[QUOTE=inovermyheadd]oh right....I apologize...I meant deleting files I installed from .bins and .runs[/QUOTE]
in that case, yes you should be able to remove the relevant directories and be OK.  just be sure that you don't mess up any dependencies.

---

### Post by inovermyheadd on 2006-03-14
ok, thanks!

---

