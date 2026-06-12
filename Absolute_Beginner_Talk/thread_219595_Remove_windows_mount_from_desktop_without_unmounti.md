---
title: "Remove windows mount from desktop without unmounting?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-07-20
I want my windows mount off of my desktop (because I hardly use it) but I do not want to unmount my partition.  When I right-click on the icon I am unable to delete, I'm not sure what else I can do.  

Thanks for your help!

---

### Post by swamytk on 2006-07-20
$ gconf-editor

You will be shown gnome configuration editor window. select app->nautilus->desktop->volumes-visible set to false. (uncheck it). This way you enable/disable appearance of computer,home,trash also. 

Note: I suspect whether USB stick will be displayed on screen automatically when you diable this feature? If you know let me be informed here.

---

### Post by Getwild2 on 2006-07-20
> **swamytk said:**
> $ gconf-editor

You will be shown gnome configuration editor window. select app->nautilus->desktop->volumes-visible set to false. (uncheck it). This way you enable/disable appearance of computer,home,trash also. 

Note: I suspect whether USB stick will be displayed on screen automatically when you diable this feature? If you know let me be informed here.
Great, thanks!!  I've been here before, just didnt know how to find it.  ](*,)

---

