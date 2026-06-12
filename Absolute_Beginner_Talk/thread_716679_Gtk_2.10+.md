---
title: "Gtk 2.10+"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Stu09 on 2008-03-06
I tried to install the Aurora engine so I could use the themes featured in this month's desktop thread. 
It told me I need GTK 2.10+  
Where do I find this ? Is it in the repos ? 

PS I'm running Gutsy.

---

### Post by justleen on 2008-03-06
on gutsy you already have a>  GTK+ 2.10 
you can find out by checking the installed packages
```

 dpkg-query -l |grep -i gtk

```
this returns :
libgtk2.0-0  -----     2.12.0-1ubuntu3    -----   The GTK+ graphical user interface librar

---

