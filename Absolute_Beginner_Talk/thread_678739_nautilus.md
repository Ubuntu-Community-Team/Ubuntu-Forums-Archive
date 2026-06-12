---
title: "nautilus"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-26
how does the nautilus command work?  i understand it is represents the graphical file browser component of GNOME, but what does the nautilus command actually do?  please provide an example if possible.  thanks.

---

### Post by spiderbatdad on 2008-01-26
```
man nautilus
man -k nautilus
``` use the arrow key to scroll the pages. press Q when done, to return to command prompt.```
nautilus --help
```

Press F1, then search nautilus.

---

### Post by Mr. Eddy on 2008-01-26
nautilus is indeed a graphical file browser similar to explorer in microsoft windows. Since nautilus is a graphical aplication it doesn't make sense to use it in a terminal.

however, you can start nautilus from terminal by typing nautilus.

Sometimes I start nautilus from terminal to gain root rights in nautilus. I type in terminal 'gksudo nautilus'. But this is not recommended.

hope this helps

---

### Post by Promaster91 on 2008-01-26
```

sudo nautilus

```

This will run nautilus with admin access.

---

### Post by Matt26 on 2008-01-26
thanks- so what would be the difference between running 'sudo nautilus' and 'gksudo nautilus'?  what do each of these commands do?

---

### Post by philinux on 2008-01-26
gksudo nautilus gives you full (root) access to all files including system files. You can break your system if you delete the wrong file etc. But it is essential in some instances.

---

### Post by Faud on 2008-01-26
The difference between sudo and gksudo can be found here

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Mr. Eddy on 2008-01-26
the difference is, if you want to start a graphical application via terminal you need to use gksudo (g stands for graphical). If you want to gain root rights in terminal yo just use sudo. for graphical aplications in some circumstances there are issues using sudo. Thats why you need to use gksudo for graphical applications

---

