---
title: "Have no rights in var/www"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by Enter on 2005-12-24
ok  all files there belong to root so i cant just cahge them or paste something  to copy/paste something there i need to use the terminal, when i changed the owner via terminal it only changes it for one file so when theres a lot of files..
i searched in the guide but couldnt find anything

Anyone help please :D

---

### Post by Koybe on 2005-12-24
use chown as this for recursion :
```

chown -R username. /var/www
```
It will change the owner of the directory and all the files below.

---

### Post by Enter on 2005-12-24
i think i dont that and it only changed the owner of the folder :D

edit// w00t it worked thanks
but i recall using this command and it only affected one file

---

### Post by Koybe on 2005-12-24
I guess you made an error, I'm sure this is working ;)

---

### Post by sudharshan on 2005-12-24
you must have missed the '-R' standind for recursive

---

