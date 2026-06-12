---
title: "initng starting problem"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-04-04
I've been installing the initng perfectly (as I hope) and added the entry in the menu.lst. If chosen at the boot menu, initng boots until a login screen appears, where i login, but then i do not know what to type in, to switch to ubuntu. In an older post it was suggested, to type "sudo ng -update add hald cupsddefault" which yields either " ... is not a script" or " ... already added". Then it was said to type "ngc -x" which results in a message like "unknown command ". Do you know how ubuntu can be started from this situation? Thanks

---

### Post by idlewild on 2006-04-04
If you're at a test based login gdm isn't starting correctly. Try sudo ng-update add gdm

---

