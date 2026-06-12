---
title: "how to delete wine folder in the application"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by KeenObserver on 2007-10-04
i have uninstalled wine but there's still the folder in application for wine apps that i installed like hp printer..before i uninstalled wine, i first uninstalled the softwares on it, but it wont get uninstalled...and now i uninstalled wine hoping that all softwares installed by wine will dissapear (i use sudo aptitue purge wine) but the folder is still there...can you help me out guys...thanks

---

### Post by stchman on 2007-10-04
> **KeenObserver said:**
> i have uninstalled wine but there's still the folder in application for wine apps that i installed like hp printer..before i uninstalled wine, i first uninstalled the softwares on it, but it wont get uninstalled...and now i uninstalled wine hoping that all softwares installed by wine will dissapear (i use sudo aptitue purge wine) but the folder is still there...can you help me out guys...thanks

```
rm -r -f ~/.wine
```

---

### Post by KeenObserver on 2007-10-04
tried it but it's still there in the application...do you think rebooting my system might do the trick?

---

### Post by KeenObserver on 2007-10-04
is there a manual procedure wherein i can just delete the folder?cause its already uninstalled..i looked at /usr/bin and theres no folder or whatsoever named wine..i beginning to get confuse..help me out please...thanks

---

### Post by santiagoward2000 on 2007-10-05
Not sure about Edubuntu, but in Xubuntu, all you need to do is delete the folder from /home/username/.local/share/applications/wine/Programs. Here's some sort of manual, at the bottom it talks about uninstalled Wine Applications [http://xubuntuguide.org/tiki-index.php?page=En:Feisty&redirectpage=HomePage#Remove_Wine_menu_entries]("http://xubuntuguide.org/tiki-index.php?page=En:Feisty&redirectpage=HomePage#Remove_Wine_menu_entries"). However, I repeat, this is for Xubuntu, so I'm not 100% sure it'll work for you.

---

### Post by nowshining on 2007-10-05
i had the same problem with program, 

places - home folder

ctrl + h

.local

applications


they should be in there, just delete it - move to trash - and there is no need to reboot or anything it should auto reload itself :) and the icon and or icons should be gone.

---

### Post by KeenObserver on 2007-10-05
> **nowshining said:**
> i had the same problem with program, 

places - home folder

ctrl + h

.local

applications


they should be in there, just delete it - move to trash - and there is no need to reboot or anything it should auto reload itself :) and the icon and or icons should be gone.


Thanks...it worked..hehehe

---

### Post by nowshining on 2007-10-05
lolz like I said i had the same problem and was looking for them when I had icons that wouldn't go away, and finally found out that they were in that folder :P

---

