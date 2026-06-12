---
title: "how do i edit the xorg.conf file? i am not the owner, the owner is root??"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by adam.white on 2007-03-31
i am trying to set up my ATI radeon 200G series, and need to delete 'ati' in the xorg.conf file and replace it with 'fglrx' but i dont have permission to edit the file because it belongs to root?!? any ideas?

Thanks, Adam x

---

### Post by Henry Rayker on 2007-03-31
You need to open the file as a super-user. The command will be ```
gksudo gedit /etc/X11/xorg.conf
``` You can perform any action using either sudo or it's graphical equivalent gksudo.

---

### Post by 23meg on 2007-03-31
Use sudo (or gksudo/kdesu).

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you're using GNOME, that would be

```
gksudo gedit /etc/X11/xorg.conf
```

---

