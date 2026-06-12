---
title: "plz help me"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by CookieSlave on 2007-03-31
i got a dell's laptop and its designed for winXP and my XP kinda died...
so now i've insert the ubuntu to try and save my hard disk but the computer keep giving me a warning error that i dont have the permissions or something...
"You do not have the permissions necessary to view the contents of "disks-conf-hda5"."
can anyone help me?

---

### Post by eljalill on 2007-03-31
You can open a terminal (which you can find in the system panel) and type
gksu nautilus 
Then a new filemanager should open, which a root rights, and with which you should be able to view the contents this directory

---

### Post by CookieSlave on 2007-03-31
i know how to get to the browser i just cant get into my hard disk...

---

### Post by eljalill on 2007-03-31
sometimes sudo su brings better results than just sudo "command"

---

