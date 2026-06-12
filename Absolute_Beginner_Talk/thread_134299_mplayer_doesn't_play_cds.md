---
title: "mplayer doesn't play cds"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by lw4ul on 2006-02-21
Hey everyone this is my first post so bare with me.I benn using linux for about 3 mounths now and have just switched to ubuntu from fc4 i got mplayer and it plays movies no prob but i can't play any audio cds or files is there anything i can do to fix this?

---

### Post by gord on 2006-02-21
mplayer is primaraly a video player (allthough it might be able to do some audio stuff as well, im not sure). i would suggest using Totem or Rythembox instead to play your audio :)

---

### Post by lw4ul on 2006-02-21
ok i was using amarok that seems to work pretty good thanks

---

### Post by celloandy on 2006-02-21
```
mplayer cdda://
```
That'll play a CD.  Not sure why you'd want to, really, as any of the GUI CD players (my preference is Goobox) are easier to use, but that'll work.

Andrew

---

### Post by lw4ul on 2006-02-21
what's goobox?

---

### Post by celloandy on 2006-02-21
It's a CD player/ripper using Gstreamer: [http://www.gnomefiles.org/app.php?soft_id=531]("http://www.gnomefiles.org/app.php?soft_id=531"). Soundjuicer and Goobox were the two competitors to be the official Gnome CD player/ripper, and SJ won, but I prefer Goobox, so I use it, instead. It's in apt (Universe, I think), if you want to play with it, but Soundjuicer, which is installed by default under Gnome, should work fine, and should auto-launch when you insert an audio CD.

Andrew

EDIT: I see that you're using Kubuntu.  I don't use KDE, so I don't know the specifics of their apps, but they have a CD player, too, though I'm not sure what it's called or whether or not it auto-launches.

---

