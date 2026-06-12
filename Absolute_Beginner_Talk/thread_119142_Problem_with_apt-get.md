---
title: "Problem with apt-get"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by PzKpfw-Ragnarök on 2006-01-18
I have problem with apt-get, it wont find any program that i try to download, for example:
"sudo apt-get install conky"
it says: that packet cannot be found...
What is wrong?

---

### Post by fuscia on 2006-01-18
don't you have to add the universe repository (conky *is* in universe) in order to apt-get the program?

---

### Post by PzKpfw-Ragnarök on 2006-01-18
And how i do that, i'm complete newbie :)

---

### Post by dueY on 2006-01-18
Edit your  

/etc/apt/sources.list

Do this by typing ```
sudo gedit /etc/apt/sources.list
```

You'll have to look up the address for the repository yourself I'm lazy :razz:

---

### Post by aysiu on 2006-01-18
[QUOTE=PzKpfw-Ragnarök]And how i do that, i'm complete newbie :)[/QUOTE] See the first link of my sig.

To get a terminal go to Applications > Accessories > Terminal

---

### Post by PzKpfw-Ragnarök on 2006-01-19
Yeah, i know how to put terminal on :)
But thanks for the info mates.

---

