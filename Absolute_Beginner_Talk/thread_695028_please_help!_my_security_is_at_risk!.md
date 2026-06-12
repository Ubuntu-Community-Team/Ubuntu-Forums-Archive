---
title: "please help! my security is at risk!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by angf117 on 2008-02-12
my ubuntu will not update! i get this......
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
please give me any advice...thanks!

---

### Post by misfitpierce on 2008-02-12
dpkg --configure -a or sudo dpkg --configure -a

run in terminal under programs-accessories-terminal

---

### Post by LowSky on 2008-02-12
do what it says

in terminal type

```
dpkg --configure -a
```

---

### Post by jordanmthomas on 2008-02-12
> **LowSky said:**
> do what it says

in terminal type

```
dpkg --configure -a
```

Also, be sure to prepend a sudo in case you didn't know.
```
sudo dpkg --configure -a
```

---

### Post by misfitpierce on 2008-02-12
Yup like I said

---

### Post by jordanmthomas on 2008-02-12
woops, missed your post

---

### Post by SunnyRabbiera on 2008-02-12
Actually this error is quite common, nothing to fret about and is easy to fix

---

### Post by angf117 on 2008-02-13
problem solved,thanks all! couldnt EVER get this kind of help from micro....whoops almost said it!
does anyone know why this problem happens? have a gr8 day:):guitar:

---

### Post by oedha on 2008-02-13
stuck updating caused by cd / connection / computer itself ....( based on mine )

---

