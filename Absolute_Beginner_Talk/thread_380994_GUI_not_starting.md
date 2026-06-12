---
title: "GUI not starting"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-03-10
hi there,
              I changed my video card and now my gui wont start up....what do i do:( ...please can anyone help????

---

### Post by taurus on 2007-03-10
Wait for the system to boot.  When X is giving you an error message, press <Ctrl><Alt>F2 and log in with your name and password.  Then, reconfigure your X with the new graphic card with

```
sudo dpkg-reconfigure xserver-xorg
```

When you are done, press <Alt>F7 to get back to X and press <Ctrl><Alt>Backspace to restart X again.

---

### Post by wannabuntu on 2007-03-10
thnx mate ...will try that out...cheers

---

### Post by wannabuntu on 2007-03-10
thnx again worked like a charm. =D>

---

