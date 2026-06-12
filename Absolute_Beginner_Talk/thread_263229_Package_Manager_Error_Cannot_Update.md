---
title: "Package Manager Error Cannot Update"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by dmpo5450 on 2006-09-22
When I logon it showed that there are updates available.  When I tried to download nothing happened.  No when I try to use any package manger I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I can type dpkg in a terminal but can't find any explaination about
" --configure - a' means.

Where do I go from here?

---

### Post by mevets on 2007-02-15
wrong post

---

### Post by lamego on 2007-02-15
Open the terminal and type the command:
```
sudo dpkg --configure -a
```

---

