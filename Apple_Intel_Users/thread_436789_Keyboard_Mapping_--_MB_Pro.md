---
title: "Keyboard Mapping -- MB Pro"
date: 2007-05-08
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-08
Would someone mind sharing how they have their keys mapped out?? And what they use for trackpad (gsynaptics or qsynaptics /other)....  it would be great if someone could post a file.

I have been running beryl and I find that I cant access any of the alt+ctrl+F_key screens (for shell or for a second session of x).. and in general I think my keys are mapped incorrectly.

---

### Post by ronocdh on 2007-05-08
> **The_Giver said:**
> Would someone mind sharing how they have their keys mapped out?? And what they use for trackpad (gsynaptics or qsynaptics /other)....  it would be great if someone could post a file.

I have been running beryl and I find that I cant access any of the alt+ctrl+F_key screens (for shell or for a second session of x).. and in general I think my keys are mapped incorrectly.
Sorry I'm not in Ubuntu right now but I believe if you run **sudo dpkg-reconfigure xserver-xorg** you'll be given the chance to select your keyboard layout. IIRC, there are options for Mac keyboards. Perhaps this would be of some help to you in the meantime.

---

### Post by benanzo on 2007-05-08
Just to be sure, when you try a CTRL+ALT+F* you press the Fn key too?  I am not sure if it's the same on MBPs but on my macbook I press Fn+F* to get them.

---

### Post by The_Giver on 2007-05-17
That doenst work for me =(... sigh.. I was told it might be the fact that ctrl is mapped to be both ctrl_L and ctrl_R but the shortcut works only with ctrl_L

---

### Post by ronocdh on 2007-05-17
> **The_Giver said:**
> That doenst work for me =(... sigh.. I was told it might be the fact that ctrl is mapped to be both ctrl_L and ctrl_R but the shortcut works only with ctrl_L
Really? Fn+ctrl+alt+F2 works for me, because I've accidentally hit it while trying to remember Beryl shortcuts. =) Which keyboard layout are you using? I think I have mine set to Macintosh rather than US English.

---

### Post by The_Giver on 2007-05-17
Macbook/Macbook pro Keyboard Model... and layout US English.. I tried changing it to US English Macintosh but it gives me this error 

"Error activating XKB config"

---

### Post by The_Giver on 2007-05-17
> **The_Giver said:**
> Macbook/Macbook pro Keyboard Model... and layout US English.. I tried changing it to US English Macintosh but it gives me this error 

"Error activating XKB config"



Also.. I just found out i can't su root or log in as root at all =( only sudo works

---

### Post by benanzo on 2007-05-17
You can get permanent root terminal with:
```
sudo su
```
or
```
sudo bash
```

Here's how to allow root to login to GNOME (if that's what you're using.)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME)

---

