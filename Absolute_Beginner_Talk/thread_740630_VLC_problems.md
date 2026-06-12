---
title: "VLC problems"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by SupaNewt on 2008-03-30
So i am super new to Ubuntu and linux... a friend installed it... and VLC never quite worked right first of all the lower inch of the picture was distorted( as in the colors from a inch above it stretched out of proportion) so i went to add/remove programs and uninstalled it and then went to add/remove programs and installed it and now when i click on a movie and play with VLC... VLC opens first and then closes(without showing the picture) and then when i try again the screen turns black then the ubuntu log in window pops up( like the computer restarted)

any ideas!???

-Supa

---

### Post by SupaNewt on 2008-03-30
ok i figured out the playing a movie thing again... but does any one have any ideas about the blurry distorted bottom?

---

### Post by JoshuaRL on 2008-03-31
How comfortable are you with the command line?

---

### Post by SupaNewt on 2008-03-31
as in the terminal?

---

### Post by JoshuaRL on 2008-03-31
Yeah.  If you feel comfortable with this, try:

```

sudo apt-get remove vlc

```

Then, try:
```

sudo apt-get update
sudo ap-get upgrade
sudo apt-get install vlc

```

---

### Post by SupaNewt on 2008-03-31
nope tried it no luck

---

