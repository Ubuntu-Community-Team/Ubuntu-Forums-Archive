---
title: "take screenshot of open menu"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Nikusan on 2006-04-26
Can someone tell me how to take a screenshot while a menu is open? (For example, for showing off deskbar or Applications menu)

---

### Post by joshrobinson on 2006-04-26
[QUOTE=Nikusan]Can someone tell me how to take a screenshot while a menu is open? (For example, for showing off deskbar or Applications menu)[/QUOTE]

applications > graphics > gimp

file > aquire > screenshot

select full window or selected window
put it on 5 or 10 second wait to open up your menu how you want it
then just wait till it captures it

---

### Post by Sutekh on 2006-04-26
```
gnome-screenshot --delay <time>
```

---

### Post by engla on 2006-04-26
There seems to be many ways to do this.
Just for fun, with image magick:
```
sleep <time>; import -window root screenshot.png
```

---

### Post by Nikusan on 2006-04-26
Three replies in 20 minutes!
Thankyou, sirs

---

### Post by WackToMack on 2006-04-26
```
sudo apt-get install ksnapshot
```

Even though it's meant for KDE, I use it a lot...

---

