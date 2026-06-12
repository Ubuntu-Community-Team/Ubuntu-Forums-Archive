---
title: "gtk 2 how  to install what will it do?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by shashank on 2008-02-02
UBUNTU 7.10

QUESTIONS:
1) is it preinstalled on ubuntu?
2) how to install?
3)will it give transperency ?:lolflag:

---

### Post by x1a4 on 2008-02-02
> **shashank said:**
> 1) is it preinstalled on ubuntu?

Yes.

> 2) how to install?

```
sudo aptitude install libgtk2.0-bin
```

> 3)will it give transperency ?:lolflag:

No.  GTK is a toolkit for drawing interfaces (widgets--check boxes, text fields, menus, labels, etc) in software applications.  To have transparency your GUI's window manager must have support for it.  I use Xfce as my primary graphical interface which has native compositing support which includes true-transparency.  I also use AfterStep which has pseudo-transparency.  

EDIT: To get transparency and all sorts of other effects you might want to look into installing Compiz or Beryl.  Just search these forums there are plenty of threads about both.

---

