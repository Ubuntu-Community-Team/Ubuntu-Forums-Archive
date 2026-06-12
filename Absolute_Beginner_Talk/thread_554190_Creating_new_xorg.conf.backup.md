---
title: "Creating new xorg.conf.backup"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-09-18
i am trying to set my nvidia settings to default but it said it could not delete my xorg.conf.backup so i deleted it but now it says it cannot create a new one. so how do i create a new xorg.conf.backup as well as saving my nvidia settings to x configuration?
also on my panels the icons are all mixed up, as u can see the trash can is all the way to the left and the power button isnt at the very top right etc.
[[IMG]http://img65.imageshack.us/img65/9238/screenshotym8.th.png[/IMG]](http://img65.imageshack.us/my.php?image=screenshotym8.png)

---

### Post by amneziac on 2007-09-18
anybody?

---

### Post by CowzRule on 2007-09-18
To create a back up of your xorg.conf, from the terminal type the following```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You can simply right click on the panel icons and select "move" than move the icon with the mouse. You might have to deselect "Lock to Panel" before you can move it. Then when you got it where you want it, right click it again and "Lock it".

---

### Post by x1a4 on 2007-09-18
Run nVidia Settings with root priviledges

gksudo nvidia-settings

To move icons on the panel r-click on it and choose Move then move it.

---

