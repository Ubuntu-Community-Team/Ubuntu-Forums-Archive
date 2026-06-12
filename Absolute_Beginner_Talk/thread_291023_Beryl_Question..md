---
title: "Beryl Question."
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Dmize on 2006-11-01
Hey everyone,

   Currently I installed Beryl and Emerald and everything works smooth, once i close the beryl manager icon. I was wondering if their is a way to fix this. What happens is, when i load into ubuntu, it loads beryl into the system. But everything lags, windows flash in and out. Once i close Beryl manager (which takes about 1 minute to load a menu when its doing this), it works fine. Anyone have this issue before? If so, please help. It slows down the operating system drastically. Thanks for reading, hopefully I can resolve this.

Derek.

---

### Post by JayTee on 2006-11-01
Which version of Beryl are you using? 0.1.0 or 0.1.1? What video card are you using? One thing to try is to disable most of the Beryl plugins and then enable them one at a time to see if one of them is causing problems. There are way too many settings that could affect Beryl's operation on your computer. Remember, it's still an early beta. Check out [www.beryl-project.org](www.beryl-project.org). That's the main beryl site and there's a forum setup there you can search for issues like yours.

---

### Post by Dmize on 2006-11-01
currently using 0.1.1. I'm using a nVidia geforce 6800 ultra, It works fine once the manager is closed, but closing it seems to be the issue. Ill check their forums, think it might be the triple buffer command i put in the xorg.conf when i set it up?

---

### Post by adam.tropics on 2006-11-02
Go to System-->Preferences-->Sessions->StartUp Programs, and add

```
emerald --replace
```


Works for me anyway!

---

### Post by Dmize on 2006-11-02
> **adam.tropics said:**
> Go to System-->Preferences-->Sessions->StartUp Programs, and add

```
emerald --replace
```


Works for me anyway!

! Thanks! worked beautifully! Thanks again! :-D

---

