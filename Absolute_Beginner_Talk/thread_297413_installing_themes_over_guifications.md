---
title: "installing themes over guifications"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by chikko on 2006-11-11
a newbie question, i guess:
i've just finished installing Guifications 2.13 and there are 3 different default themes there.  the themes are localed at /usr/share/pixmaps/gaim/guifications/themes.
according to the FAQ i ran into, i should install new themes at ~/.gaim/guifications/themes/
i've downloaded some themes (tangoish, dapper, etc), and untared them into the ~/.gaim/guifications/themes/tangoish/ and ~/.gaim/guifications/themes/dapper/ accordingly, so that in each directory there are several png files, and a theme.xml file.
unfortunately, the guifications' theme menu doesn't seem to recognize my changes, even though i pressed the "refresh" button.. ](*,) 
i even tried copying the folders to the /usr/share/pixmaps/gaim/guifications/themes/ directory, right next to the default themes, but still - nada..

what am i doing wrong here??

thanks! :p

---

### Post by loko on 2006-11-12
this is due to an incompatibility.

open theme.xml and take a look at the first lines.

```
<?xml version='1.0' encoding='UTF-8' ?>
<?xml version='1.0' encoding='UTF-8' ?>
```

you have to remove one of the two lines, then it should work fine.

---

### Post by chikko on 2006-11-12
wow!  thanks alot!  working like a charm!  :)

---

