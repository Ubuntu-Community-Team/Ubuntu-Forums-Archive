---
title: "Editing Sources.list"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by rallenk on 2007-07-07
How do I acess and edit my sources.list? I think I need permission but do not know how to do that.

Thanks from a guy still learning and Lonin' It!

---

### Post by felicity on 2007-07-07
sudo gedit /etc/apt/sources.list

---

### Post by Jimmyfj on 2007-07-07
Just like felicity said - BUT be SURE you know what you're doing, you might break your system if not

---

### Post by nvteighen on 2007-07-07
> **rallenk said:**
> How do I acess and edit my sources.list? I think I need permission but do not know how to do that.

Thanks from a guy still learning and Lonin' It!

But, what are you trying to do? If you want to enable the restricted repos, you can do it this way: System -> Administration -> Software Sources. There, you'll just have to check everything on.

---

### Post by RomeReactor on 2007-07-07
> **felicity said:**
> sudo gedit /etc/apt/sources.list

Hi. I suggest you use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") for GUI applications:
```
gksudo gedit /etc/apt/sources.list
```

---

