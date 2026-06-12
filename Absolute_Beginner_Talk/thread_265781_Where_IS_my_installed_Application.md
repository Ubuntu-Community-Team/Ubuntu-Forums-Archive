---
title: "Where IS my installed Application??"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Unterseeboot_234 on 2006-09-26
Okay, Apple has an Application Folder, Win usually has a Program Folder ...
     Using Gnome Menu, I let Application -->| Add/Remove Applications install Eclipse IDE. Marvelous. It tells me I installed, no problems and found any extras I should need.
     Now, my question: WHERE is the Eclipse IDE software? It runs from the menu. I wanted to take a peek at any folder structure of Eclipse.

---

### Post by bulldog on 2006-09-26
whereis Eclipse

Before altering anything it's wise to make a backup!

---

### Post by Unterseeboot_234 on 2006-09-26
Thanks, banging around the threads in Absolute Beginner Forum, my question was answered by someone else looking for an executable. usr/bin

---

### Post by Marsolin on 2006-09-26
The best way to see where any package gets installed to is by opening Synaptic (or any other package manager) and finding the program. Highlight it and click Properties. The Installed Files tab shows the folders that every file resides in.

Alternatively this information is stored in the /var/lib/dpkg/info directly in a .list file. There is one for each installed package.

---

### Post by bodhi.zazen on 2006-09-26
or in a terminal```
which <program_name>
```

---

### Post by bulldog on 2006-09-26
> **bodhi.zazen said:**
> or in a terminal```
which <program_name>
```


Good evening bodhi.zazen

Thanks for the usefull tips.

---

### Post by bodhi.zazen on 2006-09-26
Good to see ya Bulldog.

Sorry for the delay, still at work still ya know.

---

### Post by xpod on 2006-09-26
Is it cold out?

EDIT:The debian menu is great for showing ALL app`s by the way:D

---

### Post by bodhi.zazen on 2006-09-26
> **xpod said:**
> Is it cold out?

EDIT:The debian menu is great for showing ALL app`s by the way:D

82 and sunny in Montana.

---

### Post by xpod on 2006-09-26
Phew...too hot for moi8)

---

### Post by rOOney on 2006-09-26
```
sudo dpkg -s <package-name>
```will show you a list of configuration files belonging to the given package-name.

---

