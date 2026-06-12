---
title: "Help I tried to edit menu.list but its read only"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by LastRaider on 2007-05-12
Help!! I have tried to edit my menu.list in boot/grub so windows is my first choice of booting till I learn how to do everything I need to be able to do in Ubuntu, it says I do not have permision and that it is read only. Can anyone please help me.

---

### Post by [S|G] on 2007-05-12
You need to edit as the superuser:
```
sudo gedit /boot/grub/menu.list
```

---

### Post by taurus on 2007-05-12
> **'[S|G] said:**
> You need to edit as the superuser:
```
sudo gedit /boot/grub/menu.list
```

_Please_ use gksudo with gedit.

```
**gksudo** gedit /boot/grub/**menu.lst**
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by LastRaider on 2007-05-12
cool thank you for your help.:)

---

