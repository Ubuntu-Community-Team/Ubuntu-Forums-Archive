---
title: "Root privelage"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-04-06
I need to erase a file which has root as the owner.  I tried going to the directory and pressed alt-f2, typed in sudo nautilus, and then run that command.  But it won't let me delete the file.  Is there another way to do this?

---

### Post by Najand on 2007-04-06
Press Alt+F2 and type:
```

gksu nautilus

```
enter your password and try again.

---

### Post by dbbolton on 2007-04-06
to delete files as root, run ```
sudo rm 'file'
```


be very careful when using this command.

---

