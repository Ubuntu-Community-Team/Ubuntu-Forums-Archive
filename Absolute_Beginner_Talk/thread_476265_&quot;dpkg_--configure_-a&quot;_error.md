---
title: "&quot;dpkg --configure -a&quot; error"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by drpepperdude00 on 2007-06-17
So, I just installed linux and when I try to install any new programs or updates I get this error saying I have to run 'dpkg --configure -a'. I went to the terminal and tried to run this but then is said I need "superuser privilege." what gives?

thanx

---

### Post by Outrunner on 2007-06-17
```
sudo dpkg --configure -a
```

Then type your password(it will be invisible, but don't worry, it hasn't frozen! ) ;)

---

### Post by jasmuz on 2007-06-17
Did you use "sudo"??

$sudo dpkg --configure -a

---

