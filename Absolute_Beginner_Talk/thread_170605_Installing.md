---
title: "Installing"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Manoau2002 on 2006-05-04
I asked for help installing some software from the synaptic package manager and I was sent to [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)  When I tried to install the package "menu" so that it would enable the debian option the main menu of ubuntu remained the same. (Even after the reboot) The application diagram looks different from the one on my computer and has some different options than mine. I am running ubuntu 5.10. 


                    Thanks

---

### Post by unbuntu on 2006-05-04
If you know the name of the executable file, you can add the menu item manually.  There's a menu editor I believe in GNOME that can aid you do this.  If you don't know the path to the executable file, do a ```
which *filename*
```if it happens to be in the sys path.  If not, then you can try *locate*ing any file related to the name you specified by```

locate *keyword*
```
However, in order to do this, you have to have the database created if you haven't done that already.  ```
sudo updatedb
```

This is to the extent of my knowledge anyways.

---

