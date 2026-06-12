---
title: "lol how do i get the loding screen thing"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-01-08
in kde when u log in theres a pop up splash like thing and i remember there being one in fiesty i think but ive done a few gustys on diff comp and i want it i liked it i found the one i want to, [here]("http://www.gnome-look.org/content/show.php/Ubuntux_Splash_Screen?content=70665") lol. 

will it have all the little icons

---

### Post by Kedster on 2008-01-08
lol bump

---

### Post by ryanVickers on 2008-01-08
run ```

gconftool-2 --type boolean --set /apps/gnome-session/options/show_splash_screen 1
```
and log off then on and see if it works

---

### Post by Kedster on 2008-01-08
that sorta worked but it only shwed if gor like half a second

---

### Post by ryanVickers on 2008-01-08
well, if it showed at all then it worked - any other problems are not my fault but the people who made the splash program... thats why its off by default is doesn't work very well as you can see now ;)

---

### Post by Kedster on 2008-01-08
well what happened was like it did what it used to without the splash and then did it agian with the splash 

llike can i fix that  sorr i wasnt sayying it was ur fault just that i was checking to see if theres a fix for it

---

### Post by ryanVickers on 2008-01-08
Yeah I know I'm just saying that theres only 2 options on and off and if it doesn't work good then it's the people who made it who are to blame 

I don't believe theres a fix for it unless you want to time your logon and then re-write the code so it just stays for like 20 seconds and then goes away instead of haphazardly attempting to detect progress only to fail... :p

---

