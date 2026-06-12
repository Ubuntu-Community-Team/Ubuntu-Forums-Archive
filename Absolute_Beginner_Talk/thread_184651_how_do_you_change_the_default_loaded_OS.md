---
title: "how do you change the default loaded OS?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-30
i really don't know my configuration info. I think my choose your OS screen is GRUB, my friend did everything for me. At the moment I cannot use ubuntu because I can't get the wireless to work on it (yet). I want to change the default OS to windows xp after the 10 second timeout on start up. I know this is probably sacreligious here, but don't worry it's just temporary :)

---

### Post by cskeide on 2006-05-30
```
sudo gedit /boot/grub/menu.lst
```
For example, if your grub menu shows ubuntu as the first and windows as the second alternative on the list, change the line that says "default=0" to "default=1".

---

### Post by frodon on 2006-05-30
I think that changing the order in the /boot/grub/menu.lst file should work too.

---

### Post by Iowan on 2006-05-30
You can also change the timeout value there...

---

