---
title: "Where can i access WINE?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by eighthate on 2006-06-06
I installed Wine but i dont know where i can access it, Some1 want to help me?

thx

---

### Post by beanlover on 2006-06-06
Are you trying to run something specific?  If so you can do:

$wine appname.exe

and it should kick off.

---

### Post by meng on 2006-06-06
And if you're looking for the virtual c_drive, where your windows programs will be installed to, it should be located in ~/.wine

---

### Post by echo $USER on 2006-06-06
You need to run > winecfg to create your virtual drives before you can install any .exe.

---

### Post by Jason_25 on 2006-06-06
If your lazy, the virtual drive is created on the first run of win32 app.

---

