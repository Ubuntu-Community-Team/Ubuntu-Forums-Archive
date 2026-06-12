---
title: "How to open a folder in the filebrowser with su rights [Resolved]"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by dominicd on 2007-04-11
I was wondering how I could open/browse a folder with the filebrowser with su rights.

Thanks!

---

### Post by Bachstelze on 2007-04-11
```
gksudo nautilus
```

Please be *extra* careful when doing this !

---

### Post by DaDave on 2007-04-11
I do it with Thunar File Manager by going to a command line and typing

```
sudo thunar
```

---

### Post by Bachstelze on 2007-04-11
thunar is in XFCE and please use *gksudo* to run GUI apps as root.

---

### Post by DaDave on 2007-04-11
> **HymnToLife said:**
> thunar is in XFCE and please use *gksudo* to run GUI apps as root.

Yes, Xfce - xubuntu.

Why gksudo?

---

### Post by aysiu on 2007-04-11
It should be ```
gksudo thunar
``` and **not** ```
sudo thunar
``` Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dominicd on 2007-04-11
Thanks guys!

---

