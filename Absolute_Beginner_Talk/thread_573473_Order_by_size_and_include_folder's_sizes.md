---
title: "Order by size and include folder's sizes"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-11
Is there a way to order the files in a folder (from output in terminal or from nautilus) so that they are ordered by size, but the size of the folders also is used as reference?

---

### Post by aktiwers on 2007-10-11
If I remember currect, Thunar file manager kan do this.. try it out:
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by Fixman on 2007-10-23
Well, you don't remember correctly then.

---

### Post by aktiwers on 2007-10-23
Okay, sorry about that.. then in Terminal, cd to the folder containing your files and type:
```
ls -a -S  -s
```Remember Terminal is CaSe SenSiTiVe..

EDIT: Argh! Sorry.. forgot the folder part here.. that you wanted to list them inside a folder..
In Nautilus, just rightclick and pick "Arrange Items by" and then pick "By Size", but then again.. folders dont follow here for some reason? :S

---

