---
title: "Can't edit sources.list?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Tails Prower on 2006-08-11
I just upgraded to breezy badger to get automatix, and now I can't edit the sources.list file. I never have before, so maybe I'm making some sort of obvious blunder or something. Check this out...


tails@Taurus:~$ sudo gedit /ect/apt/sources.list

this brings up a blank gedit file and says 'file created' at the bottom. I figured It was because I wasn't root user (breezy doesn't seem to have a root terminal...) so i tried a little of this:


tails@Taurus:~$ chmod 777 /ect/apt/sources.list
chmod: cannot access `/ect/apt/sources.list': No such file or directory
tails@Taurus:~$ sudo chmod 777 /ect/apt/sources.list
chmod: cannot access `/ect/apt/sources.list': No such file or directory
tails@Taurus:~$ ?!??!?!?!?!?

the file doesn't exist for this user. I tried making a new account with the in the administrator group, but that gave me the same response. Is there a root terminal I can get to?


(edit: also, there IS a file named sources.list at that locale, and it IS the sources.list file, not the one i just made.)

---

### Post by powder on 2006-08-11
Try *cat /etc/apt/sources.list*.  Do you receive any output?

---

### Post by msak007 on 2006-08-11
You're trying to edit /**ect**/apt/sources.list - the directory **ect** doesn't exist, it's **etc**. It's simply a typo, try again with the proper path and use gksudo instead of sudo to open a graphical app, like this:

```
gksudo gedit /etc/apt/sources.list
``` 
and see if that lets you edit the file.

---

### Post by PingunZ on 2006-08-11
sudo nano /etc/apt/sources.list

---

### Post by Tails Prower on 2006-08-11
tails@Taurus:~$ gksudo gedit /ect/apt/sources.list
(gedit:10453): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

this just opens another blank file, as does the nano command, and cat cannot find the file. is there a way that I could edit permissions on the file? I've tried chmod with no success, as viewed in first post...

---

### Post by Jagot on 2006-08-11
You keep putting ect - it is not ect - it is etc - change the t and the c around.

---

### Post by Tails Prower on 2006-08-11
tails@Taurus:~$ gksudo gedit /etc/apt/sources.list

(gedit:10585): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


this still gives me the same error message and blank file. but you got me, it is etc, not ect.

---

### Post by Jagot on 2006-08-11
Just try it with sudo now:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by Tails Prower on 2006-08-11
Eureka! Thank you, sir. You are a gentleman and a scholar.

---

### Post by Frank Golden on 2006-08-11
> **Tails Prower said:**
> Eureka! Thank you, sir. You are a gentleman and a scholar.
Thank you for posting your typo. We could have wasted a lot of your time trying to figure out why you were having problems. glad you got it sorted out.

---

