---
title: "Ubuntu desktop"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by bhoughton on 2006-07-28
Hello

Quite new to Ubuntu 6.06 (finished installation a few moments ago) but not as new to Linux (Ubuntu just replaced FC5 after one too many headaches).

How do I create the alias' on the desktop to take me to the trash, home and computer (each of course opening Nautilus)?  They were not created by default and it is something I want to carry over from FC5.

Regards,

---

### Post by beniwtv on 2006-07-28
You could add launchers.

e.g nautlius computer://, nautilus /home/username

Hope it helps.

---

### Post by jimmygoon on 2006-07-28
Alt+F2

type "gconf-editor" <ENTER>

Find the keys:
/apps/nautilus/desktop/trash_icon_visible CHECK
/apps/nautilus/desktop/home_icon_visible CHECK
/apps/nautilus/desktop/computer_icon_visible CHECK

---

### Post by bhoughton on 2006-07-28
Thanks for the tips.  Really liking the Ubuntu experience so far.

Regards,

---

