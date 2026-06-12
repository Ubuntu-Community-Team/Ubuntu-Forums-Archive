---
title: "5 button mouse permisson denied"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by confused! on 2008-02-10
Have been trying to change the /etc/X11/xorg.conf file to up the number of buttons on my mouse to 7 (as it counts the mouse wheel as 3). But it won't let me change it in the terminal nor through text editor (can't save anyway). Any ideas?

---

### Post by Nepherte on 2008-02-10
you have to edit the file with root permission:
```
sudo gedit /etc/X11/xorg.conf
```

---

