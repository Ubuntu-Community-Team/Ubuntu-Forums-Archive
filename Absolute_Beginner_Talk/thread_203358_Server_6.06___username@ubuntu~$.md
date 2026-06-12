---
title: "Server 6.06   username@ubuntu:~$"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by GarethL on 2006-06-25
Hello,

I have just installed Ubuntu Server 6.06 LAMP. After logging in with username and password I get this prompt on a black screen with white text:

username@ubuntu:~$

I was expecting to see a desktop. Can anyone help with this?

Gareth.

---

### Post by bikeboy on 2006-06-25
The server edition was designed that way, because you want all the computer's resources being put to use and not being wasted on a graphical desktop.

If you're were intending to use the computer as a desktop download the desktop iso, if you want a server you "could" install gnome (this will essentially give you the same result as the desktop iso) ```
sudo aptitude install ubuntu-dekstop
```
Or kubuntu-desktop, or xubuntu-desktop (lightweight).

But you might be better off installing webmin for a server if you really want graphical admin. I have and it works well.```
sudo aptitude install webmin
```
Hope that helps.

---

