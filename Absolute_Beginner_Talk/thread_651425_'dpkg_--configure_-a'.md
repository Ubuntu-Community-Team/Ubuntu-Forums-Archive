---
title: "'dpkg --configure -a'"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-27
When I try and run that command in a terminal it says its not found..(I wanted to reinstall pidgin after trying kopete) I also tried doing 'sudodpkg --configure -a' and the same error..Im wondering what I did wrong...

---

### Post by p_quarles on 2007-12-27
Why not just:
```
sudo apt-get install pidgin
```
?

---

### Post by overdrank on 2007-12-27
> **sox fan Matt said:**
> When I try and run that command in a terminal it says its not found..(I wanted to reinstall pidgin after trying kopete) I also tried doing 'sudodpkg --configure -a' and the same error..Im wondering what I did wrong...

Try ```
sudo dpkg --configure -a
``` just copy and paste the command

---

### Post by OffAxis on 2007-12-27
can you run any dpkg command?
```
dpkg
```
should at least return with the help options...

---

### Post by sports fan Matt on 2007-12-27
P_Q,

honestly wasnt thinking..LOL..just got back to the city and been on the roads in the minneapolis area for Christmas and it just slipped my brain..LOL

BTW:  hope all of you had a very merry Christmas..i did

---

