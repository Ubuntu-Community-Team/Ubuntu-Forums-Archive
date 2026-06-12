---
title: "How can I do this from the console?"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by maxsideburn on 2005-07-13
Somehow by messing around in my root account I managed to change the permissions of my normal account's home folder. What commands will I need to log into recovery mode and change those permissions back?

---

### Post by BigCdaAnswer3 on 2005-07-13
[QUOTE=maxsideburn]Somehow by messing around in my root account I managed to change the permissions of my normal account's home folder. What commands will I need to log into recovery mode and change those permissions back?[/QUOTE]

when you reboot hit escape to get into the grub menu, and select recovery mode from there. once you're there at a root console:

chmod xxx folder/

replace x's with proper permissions

---

### Post by desdinova on 2005-07-13
Once you're in the console

man chmod

man chown

will give you the permissions you need for your home folder

---

