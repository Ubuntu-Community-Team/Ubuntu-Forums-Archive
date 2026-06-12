---
title: "Changing tsk bar and stuff"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-22
Id like to know how you change the way the desktop and stuff is presented...I have what ububtu came with, but Id like to know how i can change it up.  I attached a link, this is not what im wanting per say, but id like to know how  to custumize it. I hope this question makes sense.

Thanks in advance, and may the eternal sun shine on you...

---

### Post by aysiu on 2006-07-22
No, you're not making sense. Describe in detail one thing you're trying to do, and we'll help you to achieve that.

---

### Post by GuitarHero on 2006-07-22
well you can right click and hit properties to change colors and transparency.  and you didnt attatch a link

---

### Post by mbrang00 on 2006-07-22
Damm, I alway manage to screw stuf up :)

[http://www.riveonline.com/data/phoo/2006_01_18/ubuntu.png](http://www.riveonline.com/data/phoo/2006_01_18/ubuntu.png)

If you look at that desktop and compare it to mine, it has all kinds of bells and whistles that look neat. 

Attaching screenshot of mine


I guess what i want to know is, how do i display all of the system info like that and how do i change the task bar to look like that, sor just somthing differnt

---

### Post by aysiu on 2006-07-22
It looks as if you just want gDesklets, a transparent panel, and some new icons.

Make sure you have the Universe repository enabled. Then ```
sudo aptitude update
sudo aptitude install gdesklets gdesklets-data
```

Right-click on the panel, select Properties > Background > Solid Color and change the transparency bar (slide it back and forth).

Go to [http://www.gnome-look.org](http://www.gnome-look.org) and download an icon theme. Do not unzip it. Leave it as is. Go to System > Preferences > Themes and drag the .tar.gz in the window.

---

### Post by mbrang00 on 2006-07-22
Ill give it a shot...thanks

---

