---
title: "help! how do i install a .msi file???"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by pugofdestiny on 2008-03-31
any ideas?

---

### Post by smartboyathome on 2008-03-31
You have to use WINE. What do you need it for?

---

### Post by Rocket2DMn on 2008-03-31
Assuming your program works under wine and you have wine installed, you would do
```
wine msiexec /i *installername*.msi
```

---

### Post by pugofdestiny on 2008-03-31
im installing steam but for some reason there new installers are msi format and not exe format ive been noticing alot of msi formats recently i hate msi formats im too used to exe's lol

---

### Post by Rocket2DMn on 2008-03-31
Yeah, you would run
```
wine msiexec /i SteamInstall.msi
```

---

### Post by Tatty on 2008-03-31
> **pugofdestiny said:**
> im installing steam but for some reason there new installers are msi format and not exe format ive been noticing alot of msi formats recently i hate msi formats im too used to exe's lol

.msi files should work just as well in windows as .exe's.  I remember reading an article last year about how microsoft wants to push .msi installers more for some reason i cant remember. Theyre supposed to be better than .exe for some reason.

As said in previous posts, you will need to use wine to install windows software in ubuntu.

---

