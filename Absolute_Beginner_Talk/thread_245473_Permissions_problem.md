---
title: "Permissions problem"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Capra on 2006-08-27
i cant copy a file to the user folder cuz its says "You do not have permissions to write to this folder"  anyone know how to fix this?

btw: how do i take a screen shot with the keyboard?

---

### Post by aysiu on 2006-08-27
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Tarvok on 2006-08-27
By "the user folder" do you mean /usr?

If so, what are you trying to copy there? I would recommend against changing permissions, and instead use sudo to do whatever copying you need to do at the moment. Either:

sudo cp <filename> /usr

or

sudo nautilus

for a graphical interface.

The permissions are as they are to keep people from breaking your system.

---

### Post by aysiu on 2006-08-27
I would use *gksudo nautilus* instead of *sudo nautilus*. It's just a good habit to get into.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Capra on 2006-08-27
i did it with gksudo nautilus thing, thx for the help guys :D

---

