---
title: "How do you change read/write permissions in fstab?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-18
Hi,

Trying to mount an old IDE drive so I can use it as a back up and what not.  I've managed to mount it ok, but I can't write to it.  Here's what I got in the fstab:

[B]#
#mounting IDE
#
/dev/hdc1 /media/ide auto defaults 0 0
[/B]

I thought the "defaults" option would automatically allow me to write to it as well.  Whenever I try to delete the old data on it I get  "cannot be deleted because you do not have permissions to modify its parent folder."

Thanks for the help!
-B

---

### Post by abu-fatu on 2007-03-18
go here[http://www.psychocats.net]("http://www.psychocats.net")

---

### Post by STREETURCHINE on 2007-03-18
```
gksudo gedit  /etc/fstab
```

will open fstab so you can edit the fstab.

and defaults should be 0  1

---

### Post by marmaladejackson on 2007-03-18
Thanks guys... that psychocats tutorial answered almost all my questions.  And a few I didn't even know I had!

-B

---

