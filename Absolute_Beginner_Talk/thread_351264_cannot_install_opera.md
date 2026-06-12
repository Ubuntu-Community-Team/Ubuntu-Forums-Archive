---
title: "cannot install opera"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by pluskwa on 2007-02-01
Hallo, i tried o install opera but sth went wrong
now when i try to do it i get a message
conflict with installed package
i tried to remove it but even than I get the same error
?????
an clues

---

### Post by taurus on 2007-02-01
What command did you run and what is the exact error message that you got?

---

### Post by pluskwa on 2007-02-01
Ok, i solved it but i have an old launcher in applications/internet and i don know how to remove it

---

### Post by bruenig on 2007-02-01
```
ls /usr/share/applications | grep opera
```
Paste the output in here.

---

### Post by pluskwa on 2007-02-02
I've made one launcher by myself and i want to del only this one,
the other is ok


here what i get whent i tip
cis@cis-laptop:~$ ls /usr/share/applications | grep opera
opera
opera~
opera.desktop

---

### Post by jd65pl on 2007-02-02
To remove an icon from your menus right click on the menu and choose edit menu, then you should be able to find the rest yourself

---

### Post by pluskwa on 2007-02-02
On right click I can only add the icon to diff. places 
del not possible...

---

### Post by jd65pl on 2007-02-02
NO right click on applications [the menu] not the object within the menu

---

### Post by pluskwa on 2007-02-02
thanks, well done

---

