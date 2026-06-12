---
title: "how can i add new items in Menu for all users on my ubuntu"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by tican on 2007-10-06
Hello,

I'm a new Ubuntu user and i have a question:
how can i add new items in Menu for ALL users on my Ubuntu.
Thanks,

---

### Post by Gwasanaethau on 2007-10-06
I'm not entirely sure, but you might be able to do it using:
```
gksu alacarte
```
Other than that, I haven't got a clue - sorry. :(

---

### Post by tican on 2007-10-06
Thanks for your reply,
But it doesn't works for another user . It's only work for myself.
thanks anyway

---

### Post by Lord Illidan on 2007-10-06
You want this : [http://www.gnome.org/projects/sabayon/](http://www.gnome.org/projects/sabayon/)

---

### Post by tican on 2007-10-08
Thanks for your reply,
It's look good ( the sabayon ). I'm gonna try it.
But i wonder if there's a natural way ( bij Ubuntu it's self ) to customize the user's standard profile.
I mean just 1 standard profile for everyone. And only the root can add/remove the items on the menu.

thanks very much for your help.

---

### Post by Perfect Storm on 2007-10-08
```
sudo nano /usr/share/applications/<NAME>.desktop
```

add:
```
[Desktop Entry]
Name=Alien Swarm
Comment=Alien Swarm is an overhead view tactical squad-based shooter for UT2K4.
Exec=sh /usr/local/games/ut2004/AlienSwarm/Alien-Swarm-Linux
Icon=/usr/local/games/ut2004/AlienSwarm/alienswarm.png
Terminal=false
Type=Application
Categories=Application;Game;
```

Note this is an example on a game called Alien Swarm. You need to change stuff to fit your launcher.

---

### Post by tican on 2007-10-08
Thanks Artificial Intelligence  Artificial Intelligence,

This is what i'm meaning/looking for.

Thanks you very much.

---

