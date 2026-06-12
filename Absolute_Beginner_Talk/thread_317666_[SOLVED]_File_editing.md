---
title: "[SOLVED] File editing"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-12
I need some help with editing a file. 

The file is a driver in the "etc/cups/ppd dirctory. I know what I want to change. It defaults to A4 paper now and I want to change it to Letter. I can make the changes but I cant save the file after editing it. I changed the permissions but it didn't help  (WHY)

I copied the original file to another place and made the changes then saved it That worked but when I tried to copy it back to the etc/cups/ppd directory Murphy came along and said no can do.  (WHY)

Any suggestions without getting to deep in something I know very little about.

Thanks

---

### Post by 23meg on 2006-12-12
Use sudo / gksudo. 
```
gksudo gedit /etc/cups/ppd/filename
```
As a regular user you don't have write access to files outside your home folder; the custom is to use sudo to temporarily get root privileges to carry out such tasks.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by squrl on 2006-12-12
I have tried to log in as root and when the OS was installed I am sure I gave a password for root but now it wont accet it. Did I screw up or ???

That didn't work it says there is no basis to let me in that file. lol. Guess it told me huh.

---

### Post by 23meg on 2006-12-12
The root account is disabled by default in Ubuntu. You don't have a root password by default; the preferred way is to use sudo with your user password. You don't have to log in as root, and that's advised against. Read the page I linked to above for more information.

---

### Post by 23meg on 2006-12-12
> That didn't work it says there is no basis to let me in that file. lol. Guess it told me huh.What's the exact error you get when you enter```
gksudo gedit /etc/cups/ppd/filename
```?

---

