---
title: "Put a shortcut to a partition in a panel?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-11-20
I would like to put a shortcut to open a partition on an external drive (with Nautilus) in my gnome panel. 

The partition path is /media/Active Projects

As you can see, there is a space in the name 'Active Projects' which makes it more complicated.

I searched the forums first, but the space part is the spanner in the works.

Thanks,
Trisha

---

### Post by anaconda on 2007-11-20
Right-click on the panel and select the "add to panel", and from there select the custom application launcher, and give it a name, and then for the command type this
```
nautilus "/media/Active Projects"
```

Dont forget to select a nice icon for the launcher..

---

### Post by CatKiller on 2007-11-20
Otherwise, **/media/Active\ Projects** will also work.

---

### Post by daengbo on 2007-11-20
I'm curious. You can't just plug the drive in, then drag the entry from the "Places" menu onto the panel? That seems to work for me.

---

### Post by trishacupra on 2007-11-21
Thanks - that worked great.

And no - just dragging to the panel doesn't work. It seems to at first, but after logging out it stops functioning.

---

