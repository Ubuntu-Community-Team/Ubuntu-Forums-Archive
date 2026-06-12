---
title: "Can't start Ubuntu!!! HELP!!!!"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by ferronrsmith on 2007-05-02
My computer needed some updates that were not available in the ubuntu repository, so i used a debian repo but it had dependency problems to install. I uninstaled a file called libc++c6 which is linked to gcc4. After i accidentally unistalled these files no applications seem to be running because it could not find the gcc v4.2.0. I restarted te computer and the same problem still occur, the x server (kde interface) is not even loading, it keeps reverting to console login mode. I login and tried startx, but it gives me two errors.
 
 
 could not start kstartupconfig
 could no start kdeinit
 
 When i try to load any program from the terminal it keep saying that "GCC 4.2.9 VERSION NOT FOUND" and is required by /usr/lib/libgcc....
 
 PLease HELp Me. I need back my beautiful Ubuntu.
 
 
 AWU... (Anti-Windows Users)

---

### Post by zvacet on 2007-05-03
**programs>accessories>terminal**


```
sudo aptitude install libc++c6
```

How can it be that your system need updates outside of Ubuntu?Did you add some other repositories i your source list?If you did,why didn´t you go first to the system<administration<software properties(or somrthing similar in KDE) and chek all boxes.That way you will have all repos open and all updates will come to you.

---

