---
title: "how to play avi"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by spanerman on 2007-12-04
ive tryed to play AVI in totem , it trys to instal codecs then says 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


what can i do?

---

### Post by scxtt on 2007-12-04
did you try doing what it tells you to do?

sudo dpkg --configure -a

---

### Post by spanerman on 2007-12-04
it says i need to be a superviser.....

---

### Post by Joeb454 on 2007-12-04
open up the terminal and type ```
 sudo dpkg --configure -a
``` like it says

It will ask you to put in your password (this is just the password you log on with normally) and then you should be able to play them...if not just post back :)

---

### Post by scxtt on 2007-12-04
> **spanerman said:**
> it says i need to be a superviser.....using sudo would take care of that, unless you're not using an account w/o sudo access ... was this account created during the install of the OS?

---

### Post by spanerman on 2007-12-04
yes this is the main account....should have all privalages

---

### Post by scxtt on 2007-12-04
can you copy/paste the text into here when you run?:

sudo dpkg --configure -a

---

