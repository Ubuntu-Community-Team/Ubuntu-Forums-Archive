---
title: "Rhythmbox won't startup"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-04-09
Like the title reads, it just won't start up.  The terminal command for it hangs as well.  What should I do?

> : $ rhythmbox
l

i386
Gutsy Gibbon

Sugi

---

### Post by Crafty Kisses on 2008-04-09
Have you tried uninstalling Rhythmbox?
```
sudo apt-get remove rhythmbox
```
Then you would do:
```
sudo apt-get install rhythmbox
```

---

### Post by Sugi on 2008-04-11
Yea..... I uninstalled rhythmbox and reinstalled it.  It didn't do anything. :-/  Whats the next action?

Sugi

---

### Post by Sugi on 2008-04-11
Bump

---

### Post by stchman on 2008-04-11
> **Sugi said:**
> Like the title reads, it just won't start up.  The terminal command for it hangs as well.  What should I do?



i386
Gutsy Gibbon

Sugi

Open a terminal and type rhythmbox.  Lets see if it gives any information.

---

### Post by Sugi on 2008-04-12
before reinstalling rhythmbox:

> user: $ rhythmbox
l

after reinstalling rhythmbox:

> user: $ rhythmbox
l

Sugi

---

### Post by Sugi on 2008-04-12
After reinstalling it and trying to load up rhythmbox, it just hangs.  If I click on the rhythmbox's icon, ubuntu says it's starting up but that failures.  If I try the terminal, it says,
'user: $ rhythmbox
l'
It hangs like that.  Though, I have notice it starts up some times, but thats like 1 out of every 20 times.  I don't know how to fix this.

*Mobile Post*

Thanks,
Sugi

---

### Post by NightwishFan on 2008-04-12
try this:
```
killall rhythmbox
rhythmbox
```
It it wont start then: 
```
sudo apt-get update && sudo apt-get purge rhythmbox && sudo apt-get autoremove && sudo apt-get install rhythmbox
```
Then see if it runs.

---

