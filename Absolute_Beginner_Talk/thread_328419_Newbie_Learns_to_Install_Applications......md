---
title: "Newbie Learns to Install Applications....."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Panganat on 2006-12-30
This is a follow up to a previous post.  I have a dual boot system XP and Ubuntu -two separate HDD. (1) I downloaded Google Earth to my desktop (GoogleEarthLinux.bin)  (2)In my attempts to install the it i was advised to "cd" to desktop and use the command "sh ./GoogleEarthLinux.bin". I attempted to "cd" to desktop but it wold not so, i created a directory "mkdir" called it desktop and ran the "sh" command string and it installed ok. (3) I downloded another application to desktop and attempted to install it. tried to "cd" to desktop but ist says the directory is not there.  i "ls" and it shows two desktop directories "Desktop" and "desktop" Why will it not go to dektop.

---

### Post by d3v1ant_0n3 on 2006-12-30
```
andi@andi-laptop:~$ cd Desktop
andi@andi-laptop:~/Desktop$ 

```

The capital D is important

---

### Post by Sef on 2006-12-30
> The capital D is important

Linux is case sensitive.  Thus ~/Desktop and ~/desktop are two different directories.

---

### Post by riven0 on 2006-12-30
Say, wouldn't it be easier just to download GoogleEarth from Automatix???

---

### Post by Sef on 2006-12-30
> Say, wouldn't it be easier just to download GoogleEarth from Automatix???

Automatix can be easy if it works.  If not, you will likely need to reinstall Ubuntu.  A significant number of people have had to reinstall automatix because it did not work correctly.

---

### Post by raul_ on 2006-12-30
> **riven0 said:**
> Say, wouldn't it be easier just to download GoogleEarth from Automatix???

I don't see how...i personally hate Automatix . I only used it to install the codecs. Besides, it would take a lot of time to start automatix, switch the sources.list, run that script, switch to the original sources.list, just to install one program. I like using apt-get :)

---

### Post by riven0 on 2006-12-30
> **Sef said:**
> Automatix can be easy if it works.  If not, you will likely need to reinstall Ubuntu.  A significant number of people have had to reinstall automatix because it did not work correctly.

:shock: Good thing I use apt-get then... 

:D

---

