---
title: "Dual boot question:  Can I give a bit more space to XP?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-08-23
I have a dual boot system, XP for games Ubuntu for everything else.  I want to give XP a bit more space so I can have more than one game at a time on it, I don't really need the space I have on the Ubuntu side.  I don't want to have to reinstall anything.   

Is there a way to do it fairly easily?

---

### Post by armandh on 2007-08-23
in xp  use partition magic or similar to resize partitions
or 
use qparted 
or
my new favorite [http://partedmagic.com/](http://partedmagic.com/)

down load and burn the live parted magic os/program
boot, click on the hard disk icon at the bottom, adjust the partitions, click apply

---

### Post by proalan on 2007-08-23
I would use the gpart program on the live CD, you need to unmount the drives/filesystems to resize them.

```
System -> Administrator -> GNOME partition editor
```

---

### Post by aberadam on 2007-08-23
Great, thanks a lot.  I'll look into them.

---

### Post by sdim on 2007-08-23
If you don't have a problem buying a very good partition program,I strongly recommend Easeus Partition Manager.It runs from Windows,and you can very easily customise how much space you want to add/remove/edit on your hard drive.It really does the job in no more than 4 clicks.

---

