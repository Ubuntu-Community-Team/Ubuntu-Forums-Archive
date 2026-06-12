---
title: "cant create folder in &quot;file system/usr/"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by bubi1980 on 2006-09-03
hi,

I would like to create a skin folder for BMP. What I do is: open file system/usr/include/bmp/ and try to create a skin folder but dont have the permission to make or change folders files.
I have the same problem in "file system/usr/share/backgrounds (to change wallpapers).
I have a password and username, am I not the root?
please help me out

---

### Post by mtn on 2006-09-03
Open a terminal window Applications>Accessories>Terminal

In the terminal windows type 
```

gksudo nautilus
```

This should give you Naitilus in root mode and let you create the folders you want!

Hope this helps

---

### Post by bubi1980 on 2006-09-03
thank you for the post (the solution)
:)

---

### Post by bubi1980 on 2006-09-03
when i open the terminal and type "gksudo nautilus" it asks me for the sudo password;
i am the only user on this computer and i created 1 username, if i fill my username password, its just not correct!!
whats the password "root" or something like that?

---

### Post by Klaidas on 2006-09-03
No, it must be your password.
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by bubi1980 on 2006-09-03
ok thx, now its working

---

