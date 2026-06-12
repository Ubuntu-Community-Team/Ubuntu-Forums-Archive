---
title: "failed to start x server"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by regularjordon on 2006-08-05
well after trying to get xgl working, i restarted my computer and when i do, i am getting these messages...

[[IMG]http://img460.imageshack.us/img460/3007/p1000352th1.th.jpg[/IMG]](http://img460.imageshack.us/my.php?image=p1000352th1.jpg)
[[IMG]http://img460.imageshack.us/img460/6030/p1000353sl2.th.jpg[/IMG]](http://img460.imageshack.us/my.php?image=p1000353sl2.jpg)
[[IMG]http://img487.imageshack.us/img487/3098/p1000354vv3.th.jpg[/IMG]](http://img487.imageshack.us/my.php?image=p1000354vv3.jpg)
[[IMG]http://img303.imageshack.us/img303/6366/p1000355ei2.th.jpg[/IMG]](http://img303.imageshack.us/my.php?image=p1000355ei2.jpg)
[[IMG]http://img309.imageshack.us/img309/4639/p1000356gg7.th.jpg[/IMG]](http://img309.imageshack.us/my.php?image=p1000356gg7.jpg)

so how do i fix this?

---

### Post by taurus on 2006-08-05
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by tseliot on 2006-08-05
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

then type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by regularjordon on 2006-08-05
i did that, and all the menues ad such, restarted and still im getting the same messages.

---

