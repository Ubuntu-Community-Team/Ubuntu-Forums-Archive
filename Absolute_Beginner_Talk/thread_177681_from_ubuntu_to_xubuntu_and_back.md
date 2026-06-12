---
title: "from ubuntu to xubuntu and back"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by skinnygmg on 2006-05-16
i want to try xubuntu, and it looks like this will get me there...

sudo apt-get install xubuntu-desktop

but what if i don't like it and want to go back

---

### Post by Perfect Storm on 2006-05-16
```
sudo aptitude install xubuntu-desktop
```


and if you want to remove it:
```
sudo aptitude remove xubuntu-desktop
```

---

### Post by Iarwain ben-adar on 2006-05-16
Hi,
normally you just logout, choose the session you want to use, and login again ;-)


Iarwain

---

### Post by sparkov on 2006-05-16
```
sudo aptitude install xubuntu-desktop
```

being the same as

```
sudo apt-get install xubuntu-desktop
```?

What's the difference?

---

### Post by Iarwain ben-adar on 2006-05-16
I heard that aptitude is easier when removing programs (it removes their dependencies or something like that)

Correct me if i'm wrong (probabely) :D


Iarwain

---

### Post by skinnygmg on 2006-05-16
thanks all :)

---

### Post by Jagot on 2006-05-16
[QUOTE=Iarwain ben-adar]I heard that aptitude is easier when removing programs (it removes their dependencies or something like that)

Correct me if i'm wrong (probabely) :D


Iarwain[/QUOTE]

Yep - aptitude handles dependencies far better than apt-get.  If you were to remove xubuntu-desktop with apt-get lots of crap would be left behind, but with aptitude it cleans it up nicely.

---

