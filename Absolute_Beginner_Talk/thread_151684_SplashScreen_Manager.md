---
title: "SplashScreen Manager"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Flanker35M on 2006-03-28
S!

 Here it comes, stupido question of the hour! ;)  I downloaded this SplashScreen Manager in the Gnome-Art package, extracted to My Downloads and in readme it says run as "sh setup.sh"..Ok fine by me but how?! Terminal does not see it and to add to the n00bness..which program or command? Thank you in advance! Oh, and got the Ubuntu 64-bit up and running with the AMD64 SMP-kernel :D Assuming SMP means dualcore or similar support :-k

---

### Post by Qrk on 2006-03-28
SplashScreen manager is in the universe repository, you can get it with
```

sudo apt-get install gnome-splashscreen-manager
```


If  you haven't enabled universe yet, please go to:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Note that if you did install the program correctly using the sh script, you can run it by typing ```
gnome-splashscreen-manager
``` in a terminal.

However, gnome-splashscreen-manager is written in ruby, so it has a lot of dependencies that Ubuntu doesn't have by default, (namely, ruby) which weren't checked by the method you tried.

---

### Post by Flanker35M on 2006-03-28
S!

 As said, never let a n00b loose in linux world ;) Worked 100% Thank you very much!

---

