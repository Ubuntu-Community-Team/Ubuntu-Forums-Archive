---
title: "what happened   to it?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by kegstand on 2006-10-05
ok i think  i did  an  improper  shut  down  on my  ubuntu, and  now   my  grafical  user  interface wont   come up i.e. my user login screen.  so now   i get  the  root@userdesktop:option  what  do i  do   now?

---

### Post by aysiu on 2006-10-05
Have you tried one of these? ```
sudo /etc/init.d/gdm restart
``` ```
sudo /etc/init.d/kdm restart
``` ```
startx
```

---

