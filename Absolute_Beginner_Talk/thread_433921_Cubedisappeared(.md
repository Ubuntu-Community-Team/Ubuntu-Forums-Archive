---
title: "Cubedisappeared:("
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by !Rami! on 2007-05-05
The cube thing on the botton right disappeared when i was entering desktop effects:(  please help this 13-yearold out, please!!!!!

---

### Post by Wiebelhaus on 2007-05-05
Right click on panel and "add to panel" drag the "cube thing" onto the panel , then lock it in place.

---

### Post by icechen1 on 2007-05-05
Try this:
in a terminal tape:
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

---

### Post by !Rami! on 2007-05-06
Thank you very much!!!!:):):):):):):)

---

### Post by ConsummateK on 2007-05-27
Sorry to drudge up an old thread...

I just had this happen to me (panicked for a second!) but luckily the forum came through again and simple search of "cube disappeared" brought up the exact solution. 

Now...I can copy and paste terminal commands all day but not learn much of anything so I was wondering if someone would take a second to explain why and what exactly happened as well as exactly what it was I did to fix it? 

I can see from the commands that I apparently just manually edited the configuration of "gconftool" to bring the effect back but was it just a normal bug that happens or did I break something?

The last thing I remember doing before it *poofed* on me was changing the application font >.<

---

