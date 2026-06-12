---
title: "Uk English Keyboard Settings"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-10
Can anyone tell me if there is a way I can import a standard UK english keyboard layout WITHOUT dead keys, it seems the one in the Ubuntu editor is correct but it has dead keys and thats annoying, choosing US layout (which it was as standard) puts certain keys the wrong way round! 

Calv

---

### Post by MyBigToe on 2006-08-10
How do you mean dead keys?
I used the UK english option in the installer and had no problems at all

---

### Post by Jagot on 2006-08-10
> **MyBigToe said:**
> I used the UK english option in the installer and had no problems at all

Same here.  Please elaborate.

---

### Post by calvinthomas on 2006-08-10
If I go to changing it within Ubuntu (I didn't set it up correctly at install, so have to set it within ubuntu), I have two options in United Kingdom, they are: Dvorak & International (with Dead Keys), I didn't know what this really was so I tried it and it seems that certain keys have to be pressed twice for them to work, such as speech marks (shift 2) you have to hold shift and press 2 twice! This is obviously a pain!

Calv

---

### Post by calvinthomas on 2006-08-10
Ok fixed, I changed it by using my X settings instead of my Gnome settings and now it works perfectly!

Calv

---

### Post by _graham_ on 2006-08-24
I have the same problem, how did you change your X settings?

---

### Post by calvinthomas on 2006-08-24
By Reconfiguring XORG type:

"dpkg-reconfigure xserver-xorg" without the quotes into a terminal and follow it through (Note this will also redo graphics aswell so beware if you have installed graphics drivers seperately you may have to redo it after this)

Calv

---

