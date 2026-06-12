---
title: "Wine installed?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by thypeacefrog on 2007-03-17
Hi I just need some help working wine. I used the add/remove programs to install wine but I can't use it, there's nothing about it in the application thing, and it doesn't pick up when I wanna install .exe's

---

### Post by ajmorris on 2007-03-17
> **thypeacefrog said:**
> Hi I just need some help working wine. I used the add/remove programs to install wine but I can't use it, there's nothing about it in the application thing, and it doesn't pick up when I wanna install .exe's

install the .exe's through the shell using; ```
wine "your.exe"
``` (do not use root as this will install it for root and not you) Also, please make note that not all applications will be able to be installed over wine as windows apps support for linux is limited.

---

### Post by thypeacefrog on 2007-03-17
When I try that I get 

jack@jack-laptop:~$ wine setup.exe
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found

---

### Post by david_kt on 2007-03-17
> **thypeacefrog said:**
> When I try that I get 

jack@jack-laptop:~$ wine setup.exe
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found

That means you setup.exe is not in your home folder (jack@jack-laptop). I guess you put your setup.exe file on desktop. In this case, what you need to do is:

jack@jack-laptop:~$cd Desktop
jack@jack-laptop:~/Desktop$wine setup.exe


The idea is to make sure you call the file from the same folder. Other wise, you need to give  the path to that file in order for wine to find that file.

Regards,
DK

---

### Post by thypeacefrog on 2007-03-17
ahhhhh okay thanks alot man

---

