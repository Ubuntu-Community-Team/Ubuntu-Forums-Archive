---
title: "where do read protected scripts go"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by r3bol on 2008-02-01
I want to make a script that is executable for everyone but not readable by normal users (unless accessed with sudo). 
Is this possible (Where does it go?)?

---

### Post by eolson on 2008-02-01
If I understand your question correctly you just set the permissions for everyone to execute only.  The script stays in it's normal place.

---

### Post by eapache on 2008-02-01
Where it goes doesn't matter, as all of the permissions are file-specific.

---

### Post by Whiffle on 2008-02-01
To make it easy to use, you can put it in /usr/local/bin and adjust its permissions accordingly.  With it there anybody can run it without having to type the directory.

---

### Post by bodhi.zazen on 2008-02-01
I advise you put your personal scripts in 

~/bin

If you want to make them available to all, link 'em

```
sudo ln -s /home/<your_home>/bin/script /usr/bin/script
```

set permissions with chmod

---

