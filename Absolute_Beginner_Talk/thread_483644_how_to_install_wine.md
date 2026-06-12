---
title: "how to install wine?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-06-25
i try ```
sudo apt-get install wine
``` 
and it says package cannot be found?

ne ideas?

---

### Post by Crafty Kisses on 2007-06-25
Make sure you have extra repositories enabled.

In the terminal, type:
```
sudo aptitude update
sudo aptitude install wine
```

---

### Post by rillip on 2007-06-25
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")  Provides instructions on how to do this using apt-get and provides a .deb if for some reason you can't get that working

---

### Post by LiNuXxToOthEMaX on 2007-06-25
> **Codename said:**
> Make sure you have extra repositories enabled.

In the terminal, type:
```
sudo aptitude update
sudo aptitude install wine
```

thanks that worked!

---

### Post by Crafty Kisses on 2007-06-25
> **LiNuXxToOthEMaX said:**
> thanks that worked!

No problem, if you have anymore issues, please post them. ;)

---

### Post by cogadh on 2007-06-25
> **LiNuXxToOthEMaX said:**
> i try ```
sudo apt-get install install wine
``` 
and it says package cannot be found?

ne ideas?

Just an FYI, you had one too many "install" options in that command. It may have been erroring on a package called "install".

---

### Post by Crafty Kisses on 2007-06-25
> **cogadh said:**
> Just an FYI, you had one too many "install" options in that command. It may have been erroring on a package called "install".

That could have been the issue too. :p

---

### Post by LiNuXxToOthEMaX on 2007-06-25
> **cogadh said:**
> Just an FYI, you had one too many "install" options in that command. It may have been erroring on a package called "install".

ya i didnt type that in the terminal sorry, i just typed in forum

---

### Post by Crafty Kisses on 2007-06-25
> **LiNuXxToOthEMaX said:**
> ya i didnt type that in the terminal sorry, i just typed in forum

Haha, no problem man.

---

