---
title: "unable to install new programs"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by tomerwe on 2008-02-22
newbie,
I installed fresh copy of ubuntu today, everything seems to be working fine. EXCEPT, I can't seem to able to use the (ADD/REMOVE) utility to add new programs. the utility fires up, and I'm able to search software. 
If I mark a program to be installed it tells me "the list of application is not available. he prompts me to refresh, i do so and it seems as if he installs/updates his lists but unmarks the program, when I choose it again the routine starts over.

I can install software manually, and the Internet connection is working. 
Any Idea what's wrong?

---

### Post by spiderbatdad on 2008-02-22
Applications>>Accessories>>Terminal```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by PeterJS on 2008-02-22
Did you have a working internet connection when you first installed Ubuntu?

The installer makes a rather dumb assuption, which will be fixed in Hardy thankfully, that if it can't find the internet right that second then clearly it never will and so it disables all the online sources for updates. To fix this if you go to System > Administration > Software Sources, you can re-enable them and try again.

---

### Post by Lisa Y on 2008-02-22
```

sudo apt-get <program>

```

---

### Post by oldos2er on 2008-02-22
Go to System, Administration, Software Sources, and make sure all the boxes  on the first page are checked.

---

