---
title: "[SOLVED] Printer prints sideways"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by kulotzy on 2008-04-04
Im very sorry for asking this question if this has already been solved but when i tried searching this topic, only a few other threads came out and i couldnt find a solution. 

...my problem is, no matter how i modify the configuration of the printer settings **my printer prints my documents sideways**, I tried uninstalling Open Office but it didnt solve the problem... What confuses me is whenever i use _a different computer, it works fine but when i use my Ubuntu Desktop PC, i am faced with this problem._

Any help is appreciated, thank you.

---

### Post by PointyWombat on 2008-04-05
Hi,

For starters, please post your printcap file:

```

cat /etc/printcap

```

As well as your printers:

```

lpc status all

```

---

### Post by kulotzy on 2008-04-07
Thanks for replying. I was able to figre it out myself.

---

