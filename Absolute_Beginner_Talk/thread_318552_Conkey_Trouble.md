---
title: "Conkey Trouble"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-14
hi guys i am on Ubuntu 6.06.1 LTS (Dapper Drake) and KDE 3.5. when i am install conky i get a error  -

abcd@root-desktop:~$ sudo apt-get conky_1.4.2_Oubuntu1_i386.deb
sudo: timestamp too far in the future: Dec 14 17:57:33 2006


what i do:(

---

### Post by taurus on 2006-12-14
```
sudo apt-get install conky
```

---

### Post by lucky_chouhan on 2006-12-14
thanks i am install successfully but problem is how start automatically and this details show left bottom screen i want right top screen how.

---

### Post by taurus on 2006-12-14
If you want conky to start when you log in, then you need to add it to your Sessions.

System -> Preferences -> Sessions -> Startup Program -> Add.

And if you want to change the way conky is behaving, then you need to edit ~/.conkyrc...

Look here for more info.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by lucky_chouhan on 2006-12-14
thanks again.

---

