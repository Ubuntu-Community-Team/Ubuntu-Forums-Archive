---
title: "Forgot gconfg editor command ?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-08-30
Yeah, anyone know the command to get into the gnome configuration editor  ? I forgot it !
Thanks :)

---

### Post by felicity on 2007-08-30
gconf-editor if I remember correctly..

I'm on my arch system so I can't test it right now

---

### Post by sdim on 2007-08-30
gconf-editor (?)

---

### Post by bashologist on 2007-08-30
You have almost 1k posts on this forum, shouldn't you know by now!? n_n

If you don't know a command, you could try tab completion in a terminal too.

---

### Post by Drakkor on 2007-08-30
Yep that's it, Thanks ! Now I thought I could find the place where you can make volumes on the desktop visible or invisible, any ideas ? Thanks again :)

---

### Post by Drakkor on 2007-08-30
Yeah, I know bash,lol :) , but awhile back I had to reinstall fiesty, and lost all my notes,lol  :)

---

### Post by bashologist on 2007-08-30
Ah, I keep notes too. Speaking of which I have that volumes visible thing written in them.
```
gconftool-2 -s /apps/nautilus/desktop/volumes_visible --type=bool false
```

---

### Post by Drakkor on 2007-08-30
Ah, so that's where it was, Thanks so much bash, I am now making a "Memos" folder,lol :)

---

