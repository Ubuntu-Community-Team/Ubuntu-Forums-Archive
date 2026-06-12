---
title: "Trouble uninstalling an incompatible application"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by BulletzBill on 2007-02-23
Hello,
I recently installed an application (Banshee 0.11.7 from [http://www.wikiupload.com/comment.php?id=85998](http://www.wikiupload.com/comment.php?id=85998)) manually from the deb file but was having problems getting it to run so I am trying to uninstall it so I can use an earlier version. However, when I go to Add/Remove Apps, Banshee is checked as installed but when I try to uncheck it, it gives me the following error:
> Banshee Music Player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type. 

Is there an alternate way to force an uninstall of an application, via a terminal for instance? (FYI I am VERY new to ubuntu and linux in general).

Thanks in advance.

---

### Post by gradedcheese on 2007-02-23
sure.  open the terminal (Applications->Accessories->Terminal) and then run:

```

sudo dpkg --remove banshee

```

(type or paste that in and press Enter).

---

### Post by BulletzBill on 2007-02-23
Awesome, that did the trick. thanks man :)

---

