---
title: "[SOLVED] cant delete from thrash can"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-07-05
my thrash can is filled with stuffs, i cant delete it .. when i try i get this error


"/home/hunki...ibs/aserver" cannot be deleted because you do not have permissions to modify its parent folder.

how do i fix this ?

---

### Post by NeoLithium on 2007-07-05
You can forcefully empty your trash this way:
```
sudo rm -fr $HOME/.Trash/*
```

---

### Post by HunkieChan on 2007-07-05
hey dude thanks.. by the way neo (the actor) and i was born on the same day :D

---

### Post by SoDanishWasLike on 2008-01-08
> **HunkieChan said:**
> hey dude thanks.. by the way neo (the actor) and i was born on the same day :D

Thanks! This worked for me too!

---

### Post by barbedsaber on 2008-01-09
please mark this thread as solved, see my sig for instructions

EDIT: or not, see post below.

---

### Post by jeffus_il on 2008-01-09
Maybe it's not solved but worked around. The may be a problem here of ownership of the home directory, OK, he managed to empty the trash directory using sudo. Why were there files in the dir that were not deletable by the owner?

---

### Post by HunkieChan on 2008-01-09
sorry, i didn't knew it could be done..yes it was solved.. i fixed it.. thanks for letting me know

---

