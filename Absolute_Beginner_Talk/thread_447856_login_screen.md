---
title: "login screen"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by naslynx on 2007-05-18
I tried to change my login screen window and when i did it i lost my login screen
1.  i change the login screen
2. i reboot with Cntrl+Alt+Back and login screen disappear
i try to reboot computer and when Grab is showing i realize what the Windows XP line is missing also
try to boot Ubuntu again
 system is working to the Nvidia windows /i am with nvidia drivers/ and after that i have black screen and pointer still working and is nothing happened
is anybody help me with this problem?

---

### Post by Najand on 2007-05-18
Push Ctrl + Alt +F1 and login.
Then try:
```

$ sudo /etc/init.d/gdm stop
$ startx

```
When X loaded, change it back to the default screen and then reboot your computer.

---

