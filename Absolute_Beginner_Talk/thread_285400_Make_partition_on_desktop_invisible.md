---
title: "Make partition on desktop invisible"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-10-26
As you can see in the screenshot,when I mounted hdb3,(Media Data),it put an icon on my desktop,it's already in "Places". How can I get rid of it ?
Thanks ! :p

---

### Post by bodhi.zazen on 2006-10-26
It is an option in the gnome pull down menu, disk management.

Unselsect the "show mounted partitions on desktop" option.

---

### Post by Drakkor on 2006-10-26
> It is an option in the gnome pull down menu, disk management.

Unselsect the "show mounted partitions on desktop" option.
__________________

Which would be located where ? :confused:

---

### Post by dbott67 on 2006-10-26
There is a setting in gconf-editor that allows the mounted volumes to display on the desktop:
```
gksudo gconf-editor
```
Browse to **APPS > NAUTILUS > DESKTOP > VOLUMES_VISABLE** (uncheck)

See [this post]("http://www.ubuntuforums.org/showpost.php?p=1666680&postcount=14") for screenshots.

-Dave

---

### Post by Drakkor on 2006-10-26
Thanks,dbott67,but the icon still is there,even re-booted,still there,maybe a bug in Edgy ? :confused:

---

### Post by dbott67 on 2006-10-26
Could be... it works as soon as I check/uncheck it.  I'm still on Dapper, though.

---

