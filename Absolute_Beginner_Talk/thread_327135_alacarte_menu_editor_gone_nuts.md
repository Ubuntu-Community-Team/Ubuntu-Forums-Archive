---
title: "alacarte menu editor gone nuts"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by rajeev1204 on 2006-12-28
hi

some programs installed in synaptic give me 2 entries , for example gnomebaker is listed in accessories and sound and video. When i remove an entry , it removes both entries together..


was working fine before. I also tried reinstalling alacarte but no use


Is this a bug?


regards
rajeev

---

### Post by bruenig on 2006-12-28
This is not alacarte's fault but gnomebaker's fault. Do
```
gksudo gedit /usr/share/applications/gnomebaker.desktop
```

Go down to the place where it says "Categories" and depending upon which menu you want to show it in delete one of the categories. So if you just want it in accessories, delete the AudioVideo part and you may also have to delete the DiscBurning part too. Or the other way around if you want it in the other place it is put. You can play around with the categories until it stays in the submenu you want.

Obviously save and then it should change in the menu.

---

