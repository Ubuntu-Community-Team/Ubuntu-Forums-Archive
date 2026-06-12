---
title: "How do you log into root in KDE?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-08
I need to delete some files in the system and I'm installing Puppy anyways so I need to just log into root ,but don't know how. I tried going to login manager and enabling root in the user section but that didn't work. Help?

---

### Post by Dr Small on 2007-11-08
Use kdesu

---

### Post by 449 on 2007-11-08
Sorry, I'm still a Linux noob and have no clue what to do with  that command.

---

### Post by tubasoldier on 2007-11-08
select Run Command from the start menu.

type in kdesu konqueror  

be very very careful. it is not a good idea to be rummaging around your filesystem as root.

---

### Post by mivo on 2007-11-08
Press Alt+F2 and type: **kdesu dolphin**  This will open the file manager in root mode.

---

