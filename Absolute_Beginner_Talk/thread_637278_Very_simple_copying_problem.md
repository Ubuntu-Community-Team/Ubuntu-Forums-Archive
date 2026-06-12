---
title: "Very simple copying problem"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Lotekx on 2007-12-10
I am trying to copy the folder AwnDeluge on my desktop  to the Deluge plugin folder.
I enter this in the terminal while in my desktop directory:

sudo cp AwnDeluge /usr/share/deluge/plugins/
 

and I get this response:

cp: omitting directory `AwnDeluge'


WHY?!? I'm not doing anything wrong, i think.

---

### Post by w7kmc on 2007-12-10
Try a  recursive copy like:

sudo cp -R  AwnDeluge /usr/share/deluge/plugins/

good luck!

---

### Post by RomeReactor on 2007-12-10
Hi. Try it like this:
```
sudo cp -R ~/Desktop/AwnDeluge /usr/share/deluge/plugins
```

EDIT: Too slow...

---

### Post by Orestes on 2007-12-10
> **Lotekx said:**
> I am trying to copy the folder AwnDeluge on my desktop  to the Deluge plugin folder.
I enter this in the terminal while in my desktop directory:

sudo cp AwnDeluge /usr/share/deluge/plugins/
 

and I get this response:

cp: omitting directory `AwnDeluge'


WHY?!? I'm not doing anything wrong, i think.

try sudo cp -r AwnDeluge /usr/share/deluge/plugins/

man cp will give you more hints.

HTH

---

### Post by nikoPSK on 2007-12-10
possibly the recursive option. 

cp -r myfile1 /directory

---

### Post by Lotekx on 2007-12-10
Thanks for all your help.

What does it mean to copy recursively, and why does it make a difference?

---

### Post by RomeReactor on 2007-12-10
It means cp will look for files inside the directory, and copy them also; if there are folders inside the AwnDeluge folder, and those folders have more files **and** folders, it will copy those too. Otherwise, without the **-R** or **-r** option, you would need to specify a particular file--inside the directory--to be copied.

---

### Post by nikoPSK on 2007-12-10
> **RomeReactor said:**
> Hi. Try it like this:
```
sudo cp -R ~/Desktop/AwnDeluge /usr/share/deluge/plugins
```EDIT: Too slow...

me too... :p

---

