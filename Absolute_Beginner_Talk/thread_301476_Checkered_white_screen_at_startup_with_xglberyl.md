---
title: "Checkered white screen at startup with xgl/beryl"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Amolad on 2006-11-17
at system startup after login my screen comes up a greyish checker pattern or about 5-10 seconds before loading gnome without beryl.

i have to manually restart beryl to get it to run, and even then it has minor misbehavior (although this could be accounted to it being somewhat experimental still).

anyone know a fix for this? im on an nvidia 6600GT card with official drivers and an athlon 64.

---

### Post by finferflu on 2006-11-17
Do you start your session as a beryl-xgl session (as suggested in the Beryl wiki)?

---

### Post by Amolad on 2006-11-17
yes, i do.

i fiddled abit and got beryl to start properly, fiddled some more and changed it from a checker to black.

but is there any way to get a picture back in there?

It feels like the checker is a fallback for if no splash screen is specified, so what i think needs done is finding where you specify the picture. I'm going to go have a look at Ubuntu's source to see how they got one up.

EDIT: found it, unfortunately xgl seems to do it differently....

it isnt worth the headache so i'll just wait untill they undoubtably fix it later on. :p

---

### Post by finferflu on 2006-11-17
Well, I solved my problem simply not starting a xgl session. I just start a normal GNOME session and then I launch beryl-manager (I put it among the startup programs). It works perfectly like that.

---

