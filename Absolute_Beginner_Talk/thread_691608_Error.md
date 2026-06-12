---
title: "Error"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Bustanut456 on 2008-02-08
Well for some reason every time i try to update or install any kind of software i get this error  message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


any help?

---

### Post by Dr Small on 2008-02-08
Have you tried running it?
```
sudo dpkg --configure -a
```

Dr Small

---

### Post by Bustanut456 on 2008-02-08
well, i don't know what to run. Do i do a search of that or something?

ohh and thanks for helping me.

---

### Post by nynoah on 2008-02-08
go to ***applications/accesories/terminal*** and type those commands in there.

---

### Post by Bustanut456 on 2008-02-08
okay i tryed that and i got this message

dpkg: requested operation requires superuser privilege


how do i make is approve?

---

### Post by nynoah on 2008-02-08
go to applications/accesories/terminal type this into it

> sudo dpkg --configure -a

it will then ask your for your password.  Put that in and it then runs that command as super user.

Sudo translates into

Su = Superuser
Do = do

so its super user command do

---

### Post by Bustanut456 on 2008-02-08
okay now for some reason it won't let me type anything in for a password, or paste.

thanks again, sorry im such a noob.

---

### Post by Dr Small on 2008-02-08
Just keep typing ;)
It's typing your password :)

---

### Post by Bustanut456 on 2008-02-08
okay i got it going thanks a lot guys.

---

### Post by nynoah on 2008-02-08
For some reason you can not use Ctrl-V to paste anything into the Terminal.  You have to L click and paste.

Then the other thing with not being able to see your password is a safety feature too keep your password secret.  Its a good thing.

---

