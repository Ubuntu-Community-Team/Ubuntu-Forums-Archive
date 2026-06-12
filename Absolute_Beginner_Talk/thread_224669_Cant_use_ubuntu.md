---
title: "Cant use ubuntu"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2006-07-28
I got my Ati drivers working and I was trying to get XGL and Compiz to work but now when I boot it goes to the login screen and then it goes to showing the startup processes. then goes to a grey screen and the mouse just sits there with is circle animation.

---

### Post by wombat20 on 2006-07-28
Your best bet is probably to get to a command line (live CD or recovery mode?) and run:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you should at least be able to get your desktop back.

I'm told that getting all that working with ATI is pretty difficult - so I haven't tried it yet!

---

