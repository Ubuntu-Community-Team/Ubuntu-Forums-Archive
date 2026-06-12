---
title: "How to install Flashplayer"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Th3Futur3 on 2006-08-20
I need to install flash player. I cant go on myspace or youtube at all. How would I install it?

---

### Post by r4ik on 2006-08-20
Try,

[http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefox)

Good luck !

---

### Post by psycosmyth on 2006-08-20
you can install it manualy from macromedia.com(not that hard)or you can use Automatix, very powerful. Just search for it and you'll see.;)

---

### Post by Ptero-4 on 2006-08-20
Hi. Welcome to Ubuntu. To get flash working you need to enable both universe and multiverse repositories. To do that go to Applications>Add/remove programs, in the window that appears click on the "show unsupported apps" checkbox and it will sohw the apps that are in universe. click on one and click install, it will tell you that it will need to enable a repository, click OK and then when the confirm install dialog appears cancel. Then click the "show unsupported comercial apps" checkbox, it shows the contents of multiverse, then click on an app from the ones that appear and do the same you did for the universe one. Then close the add/remove programs dialog, the universe and multiverse repositories are now active and will stay active. Then after that type this in a terminal window (Applications>Accesories>Terminal):
```
sudo aptitude install flash-nonfree
```
Type in your password when asked.

---

### Post by Th3Futur3 on 2006-08-20
Sorry i forgot to clarify I use Xubuntu. Will the instructions still work above? I know Xubuntu don't have add/remove programs but can i find it in the package manger?

---

### Post by psycosmyth on 2006-08-20
you Mac people scare me!:-|

---

### Post by r4ik on 2006-08-20
Try,

[https://help.ubuntu.com/xubuntu/desktopguide/C/add-applications.html#extra-repositories](https://help.ubuntu.com/xubuntu/desktopguide/C/add-applications.html#extra-repositories)

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

Hope this works.

---

### Post by kepos on 2006-08-20
> **Th3Futur3 said:**
> Sorry i forgot to clarify I use Xubuntu. Will the instructions still work above? I know Xubuntu don't have add/remove programs but can i find it in the package manger?

yes you can use that instructions, bau make shure you add extra repository. 

look [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) for howto.

---

