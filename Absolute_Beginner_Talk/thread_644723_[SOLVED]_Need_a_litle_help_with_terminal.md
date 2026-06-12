---
title: "[SOLVED] Need a litle help with terminal"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by supernoob on 2007-12-19
The folowing picture speaks for itself :
[http://img177.imageshack.us/img177/5904/ihateterminaliy4.png](http://img177.imageshack.us/img177/5904/ihateterminaliy4.png)
 
can anyone help a poor noob like me ?

---

### Post by forestpixie on 2007-12-19
doesn't seem to be a picture

---

### Post by supernoob on 2007-12-19
sorry , wrong link :lolflag: 

[http://img177.imageshack.us/img177/5904/ihateterminaliy4.png](http://img177.imageshack.us/img177/5904/ihateterminaliy4.png)

---

### Post by mike^_^ on 2007-12-19
make sure you are in the right directory, otherwise you will need to specify the full path of the folder you want to cd to.

to check your current location
```
pwd
```

changedir from another location ie from your home folder:
```
cd Desktop/myfolder
```

---

### Post by hyper_ch on 2007-12-19
Better to use:
```
cd ~/Desktop/myfolder
```

---

### Post by spadmore on 2007-12-19
In some linux shell (bash i think) you can use the tree command to see the directory tree

- Shelon Padmore

---

### Post by supernoob on 2007-12-19
Ok TNX , it works!!! :)

---

### Post by hyper_ch on 2007-12-19
or install Midnight Commander:

```

sudo apt-get install mc

```

and run it with "mc" from the shell... it's like the old DOS-based Norton Commander

---

### Post by g2g591 on 2007-12-19
tree isn't shell specific, its a program in the repos

---

