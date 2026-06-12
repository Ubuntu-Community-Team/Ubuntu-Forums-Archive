---
title: "Adding a 2nd HDD"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-11-14
I took a 40GB Western Digital out of an old Dell I have. It has Windows XP on it. I want to configure it as a 2nd Hard Drive on my Ubuntu box. I'm doing some video editing on it and need a little extra space for videos as I work on them.

When I boot to Ubuntu with both HDDs in the system, I can't see the other HDD (though, aside from "Computer", I don't know where to look). I assume I may need to repartition and reformat it. How do I do that? Do I do it from the Live CD? Can I do it from within the Ubuntu OS? How do I see it and put information on it?

---

### Post by taurus on 2007-11-14
You need to mount it before you can access it.  However, if you only use that drive in Ubuntu, then perhaps you should consider formatting it from ntfs right now to ext3.  You can do it from a terminal or you can do it using gparted in System -> Administration.  You probably need to install gparted first before you can use it since it doesn't come with a default install.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```

---

### Post by Inxsible on 2007-11-14
you can also use GParted from the Live CD.

---

### Post by siege911 on 2007-11-14
> **taurus said:**
> You need to mount it before you can access it.  However, if you only use that drive in Ubuntu, then perhaps you should consider formatting it from ntfs right now to ext3.  You can do it from a terminal or you can do it using gparted in System -> Administration.  You probably need to install gparted first before you can use it since it doesn't come with a default install.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```

OK. It's formatted to ext3, but how do I mount it?

---

### Post by Duck2006 on 2007-11-14
Have a read of this, it sould help

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

