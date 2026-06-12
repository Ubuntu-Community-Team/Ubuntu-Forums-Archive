---
title: "error while copying to &quot;/&quot; - you do not have permission..."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-20
Can someone help explain to a newbie?

I am trying to install MySQL manually based on a guide i am following. It says to move the package to /usr/local to unpack but Ubuntu is not allowing me to write to that folder. I tried in the terminal, it says "permisison denied." 

It will not be helpful to tell me not to follow this guide or suggest another one. 

I seem to be oing something wrong.

Thanks

---

### Post by bodhi.zazen on 2008-02-20
Similar topic on another thread :

[http://ubuntuforums.org/showpost.php?p=4373089&postcount=4](http://ubuntuforums.org/showpost.php?p=4373089&postcount=4)

---

### Post by spiderbatdad on 2008-02-20
use```
gksu nautilus
```

---

### Post by onthefence on 2008-02-20
THank you,
running the gksudo command worked like a charm.
Now this may be a silly question, but when I no longer want root privileges do I just close the program that I opened with the gksudo command?

---

### Post by spiderbatdad on 2008-02-21
yeppers close the root file browser

---

### Post by onthefence on 2008-02-21
Can someone explain this command? It's supposed to manually start the MySQL process.

```
bin/mysqld_safe --user=mysql --old-passwords &
```

My guess is "bin/mysqk_safe" is the process command. 
"--user=mysql" is the user initiating the process
"--old-passwords &" (I have no idea)

Thanks

---

