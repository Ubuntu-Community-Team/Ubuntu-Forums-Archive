---
title: "Why does Desktop Effects do this ( 7.10)?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-25
[http://s215.photobucket.com/albums/cc239/hilariousness16/?action=view&current=MOV00431.flv](http://s215.photobucket.com/albums/cc239/hilariousness16/?action=view&current=MOV00431.flv)


EDIT::This works now...I think

---

### Post by LinuxIsInnovation on 2007-12-25
Your link is invalid..

---

### Post by forestpixie on 2007-12-25
i get page not found with that

---

### Post by nick_h on 2007-12-25
What is the problem exactly?

---

### Post by hilariousness16 on 2007-12-25
bump

---

### Post by LinuxIsInnovation on 2007-12-25
Let me guess, you cannot run certain apps or a Video related error or some distorted graphics effects?

PS: If neither of these, please spare me :D

---

### Post by hilariousness16 on 2007-12-25
As you can see when I try to enable Desktop effects to "custom" , it loads, then automaticly goes back to "none" desktop effects, kinda annoying,worked yesterday...

---

### Post by nick_h on 2007-12-25
Have you looked in your log files for error messages?

---

### Post by LinuxIsInnovation on 2007-12-25
Looks like some error in ccsm settings. First of all, install emerald window manager for better decorations. Let emerald handle the decorations.
Btw, are your window animations working smoothly?

---

### Post by LinuxIsInnovation on 2007-12-25
Plus, try reinstalling compiz.

---

### Post by overdrank on 2007-12-25
> **hilariousness16 said:**
> As you can see when I try to enable Desktop effects to "custom" , it loads, then automaticly goes back to "none" desktop effects, kinda annoying,worked yesterday...

Why start a new thread when you have one ongoing
[http://ubuntuforums.org/showthread.php?t=649766&page=5](http://ubuntuforums.org/showthread.php?t=649766&page=5)

---

### Post by hilariousness16 on 2007-12-25
I am a huge noob...

how do i reinstall---lol

---

### Post by LinuxIsInnovation on 2007-12-25
So am I, but I know this one :D
Open synaptic, search for compiz, for all compiz related packages, click on the checkbox and select Mark for reinstallation and click the Apply on top.. Done :)

---

### Post by LinuxIsInnovation on 2007-12-25
Correction: Mark compiz only.. nothing else :)

---

### Post by hilariousness16 on 2007-12-25
ok, i reinstalled, let's see if it works

---

### Post by LinuxIsInnovation on 2007-12-25
Do you have compiz config settings mgr installed? If not, then in a terminal:
$sudo apt-get install compizconfig-settings-manager

---

### Post by hilariousness16 on 2007-12-25
it didn't work

---

### Post by hilariousness16 on 2007-12-25
i already installed compiz manager

---

### Post by LinuxIsInnovation on 2007-12-25
You need graphics drivers to support compiz. Anyway, try this:
This is valid if you are somehow running metacity.
Open terminal and type:
$compiz --replace

---

### Post by hilariousness16 on 2007-12-25
wtf this is what i got 

```
brandon@brandon-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8192): Wnck-WARNING **: Unhandled action type (nil)



```

---

### Post by LinuxIsInnovation on 2007-12-25
This is a driver problem.. No idea on ATI drivers..

---

### Post by hilariousness16 on 2007-12-25
bump:popcorn:

---

### Post by shareMenaPeace on 2007-12-25
try this howto
[http://ubuntuforums.org/showthread.php?p=3547657](http://ubuntuforums.org/showthread.php?p=3547657)

---

