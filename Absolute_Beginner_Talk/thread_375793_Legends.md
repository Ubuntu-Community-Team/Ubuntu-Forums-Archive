---
title: "Legends"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by brent_t on 2007-03-04
Hello all,
Can someone tell me how to remove the legends game? Can't find it in snaptic, add remove, and tried apt-get remove legends. I don't play this game and it is pretty big? I found where it is located and I am still in learning mode...

Thanks

---

### Post by Kobalt on 2007-03-04
Hello,
Are you talking of one of these games installed by default with Ubuntu ? If so, these games all depend of the same package : gnome-games. I'm not sure it's possible to remove only one, it's all or none...

---

### Post by brent_t on 2007-03-04
I don't believe it is in that package. I just removed gnome-games in synaptic. I didn't have any of them installed anyways but just removed the left-over files also. Legends is still there. 

Thanks

---

### Post by sirlancelot on 2007-04-06
Try typing this code below in the terminal:```
$ sudo rm -rf /path/to/legends
```Make sure to change your path. Legends doesn't install any files anywhere else.

If you are sure you will never play the game and wish to remove your settings as well:```
$ sudo rm -rf ~/.legends
```

---

