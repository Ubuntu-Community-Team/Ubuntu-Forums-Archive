---
title: "Changing language"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by brugui00 on 2007-11-28
Hey, i've  installed ubuntu today. I installed it in english, but i then wanted to change the language to "catalan". i went to language suport, and only english could be selected (and its variants). I unselected the "english" checkbox and I now can't selected again, and I have no way of changing it to catalan.

Any suggestions? Please help.

Thanks

---

### Post by jken146 on 2007-11-28
```
sudo apt-get install language-support-ca
```

This meta-package depends on all the packages you should need to have Catalan in your applications.  Select the language you want to use at login.

---

### Post by brugui00 on 2007-11-29
I am very new to ubuntu and i dont know how to use this code, or where to insert it.

plus, at the login page i can only select english, and in the language selection page, i can't select any language.

thanks

---

### Post by brugui00 on 2007-11-29
i have inserted the code  ```
sudo apt-get install language-support-ca
```

and it didnt work, i got

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-support-ca

```

??

---

