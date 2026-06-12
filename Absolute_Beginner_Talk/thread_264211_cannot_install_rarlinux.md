---
title: "cannot install rarlinux"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by eyesoftheworld on 2006-09-24
i cannot figure out how to install winrar for linux so i can unarchive my .rar files

---

### Post by wombat20 on 2006-09-24
Try Easy Ubuntu:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

That will allow you to read .rar files.

---

### Post by xyz on 2006-09-24
Make sure you've got this enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
and then just type in a console:
```
sudo aptitude update && sudo aptitude install rar unrar
```

---

### Post by qpieus on 2006-09-24
There isn't a "winrar" for linux. Rar and unrar is available, as the other messages here indicate, but those are command line versions of rar and unrar. However, after you install rar and unrar, your GUI archive manager program (I use Kubuntu, so that would be Ark, I forget what gnome uses) can read and extract rar files. So, you won't have "winrar", but you should still be able to read/extract rar files via GUI, if that's what you want.

WinRar may run under wine, but I've never tried it. No need to really...

---

