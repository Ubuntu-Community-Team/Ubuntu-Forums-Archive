---
title: "how to access lost+found?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-09-12
I'm trying to access my lost+found directory but when I cd to it I just get permission denied.
sudo doesn't seem to work either.
What am i missing?

---

### Post by por100pre1 on 2007-09-12
Excuse me but, Why do you need to access that folder? That's a folder for fsck saving damaged files. That restrictive behavior is normal. If you still want to take a look try:

```
gksudo nautilus
```

---

### Post by bodhi.zazen on 2007-09-12
You have three options ...

Easy way : ```
gksu nautilus /lost+found
```

Moderate ```
sudo -i
cd /lost+found
```

---

### Post by garyed on 2007-09-12
Thanks for the help, 
I was just being curious as to how I could access a restricted directory. 
I've done a search to find what that directory is used for but I couldn't find how to view it.

---

