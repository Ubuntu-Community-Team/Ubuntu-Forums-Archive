---
title: "Disabling Gnome on Dapper Lamp unless specified"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by kdawg22 on 2006-10-31
I recently set up a LAMP server with Dapper. I installed Gnome to have a GUI available in a pinch, however I do not want it to run everytime I start the server. How do I configure my server to run a terminal session by default and only start Gnome when I ask for Gnome?

---

### Post by dmizer on 2006-10-31
well, i know you can turn off the graphical login by going to system > administration > preferences and unchecking "gdm"

not sure if this completely disables x though.

if you want to start your grapical desktop just say:
```
startx
```

---

### Post by bodhi.zazen on 2006-10-31
[Disable GDM](http://doc.gwos.org/index.php/VirtualX#Disable_GDM)

Sorry, I did not want to type it out.

---

### Post by kdawg22 on 2006-10-31
Thank you!!! This is exactly what I was looking for.

---

