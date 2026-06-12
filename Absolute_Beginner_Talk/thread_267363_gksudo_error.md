---
title: "gksudo error"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-28
when i type [COLOR="Blue"]gksudo nautilus[/COLOR] i get an error like this...

```
sphinx@***********1:~$ gksudo nautilus
(nautilus:14246): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed. 
```

it also pops a window up of /root
inside this window the desktop folder is displayed

i thought this code would give me root access to modify files etc???

---

### Post by angkor on 2006-09-28
It's not an error but a warning. Doesn't nautilus open after that?

---

### Post by petri on 2006-09-28
> ...it also pops a window up of /root 
inside this window the desktop folder is displayed...
That one is the **root Nautilus** where you can do everything. I get that warning too in fact I get that warning everytime I use gksudo for GUI-programs. But I've been told that gksudo is better to GUI-programs and it works despite the warnings so I use it. :mrgreen:

---

### Post by uk_sphinx on 2006-09-28
thanks 
so....
how would i delete a folder i created on the desktop from this window?
dont worry i know what the file is and it wont compromise my system

---

### Post by uk_sphinx on 2006-09-28
allayluya

dont matter

---

### Post by uk_sphinx on 2006-09-28
thanks people

my first small victory

---

### Post by petri on 2006-09-28
There sure is some easy way but I do like this: in root-nautilus window I click Edit > Preferences and in tab Behaviour(?) I check the line that adds a command to popupmenu which means "Delete the file directly, don't put it in Trash". Sorry, nonenglish version :mrgreen:

---

### Post by ronmarley1 on 2006-09-28
EDIT:  OOPS!  Jeez, three posts while I was typing... sorry for the extra post...
> **uk_sphinx said:**
> thanks 
so....
how would i delete a folder i created on the desktop from this window?
dont worry i know what the file is and it wont compromise my system
The Desktop folder you are seeing in that window is root's desktop.  To delete a file from "your" Desktop, look into the folder frame in the left-hand part of the window.  You should see an icon with the name File System.  Double click it, and then you will see the "home" folder.  Double click that, and you will see the user names of the users on your computer.  Double click on the user you want, and you will see that user's Desktop folder.  Inside it is the file you want to delete.

---

### Post by aysiu on 2006-09-28
Read this page, especially the bottom bit:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by gandalf2041 on 2006-09-28
aysiu, 

excellent explanation...as always.  It seems I learn something each time I follow one of your links. Thanks! :KS

---

### Post by CatKiller on 2006-09-28
Glad to see you're making progress. Soon it'll all come into focus, and you'll be helping others.

---

