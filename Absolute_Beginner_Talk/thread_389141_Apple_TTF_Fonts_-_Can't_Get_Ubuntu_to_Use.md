---
title: "Apple TTF Fonts - Can't Get Ubuntu to Use"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by skennedy1217 on 2007-03-20
Using this tutorial...

[http://www.taimila.com/ubuntuosx.php#fonts]("http://www.taimila.com/ubuntuosx.php#fonts")

...I downloaded and installed a set of OSX fonts.  However, they don't show up under System -> Preferences -> Font.  If I browse to the folder in /usr/share/fonts/truetype/ttf, each of the font files are there, but there are red X's on each icon (showing that they are unreadable).

Is there a step I'm missing to "activate" these fonts?

---

### Post by xopher on 2007-03-20
Well if you are the only user, or you are the only one who uses these fonts, you could try copying them to ~/.fonts instead, for easier access.

Maybe there's some kind of permissions problem that makes them unreadable?

---

### Post by lamalex on 2007-03-20
the red x usually means permissions. chmod them, 777 always works :)
```
sudo chmod 777 filename
```

---

### Post by skennedy1217 on 2007-03-21
Sweet, thanks!  I ran the following and the red x's are gone...

```
sudo chmod 777 *.ttf
```

---

