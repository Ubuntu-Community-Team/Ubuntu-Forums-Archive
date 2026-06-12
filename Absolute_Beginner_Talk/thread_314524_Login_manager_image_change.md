---
title: "Login manager image change"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Turner.kj on 2006-12-07
How does one change the login manager image? ](*,)   I have been to system->Preferences->Art Manger->Art->Other Themes->Login Manager and loaded the images, but I can not install.

---

### Post by sindrum_murdnis on 2006-12-07
This is how i'v done it on edgy. Right click on system > click edit menus > Preferences > Login photo. See if this works for you.

---

### Post by mcduck on 2006-12-07
System/Preferences/About Me

---

### Post by Turner.kj on 2006-12-07
I do not have Login Photo on my in the Preferences menus.  Hmm, any idea how to fix that?

And, when I go to 'About Me" I get an error the reads: "There was an error while trying to get the addressbook information
Evolution Data Server can't handle the protocol"

This is not looking good.

btw: I am running 6.10 fully updated.

---

### Post by sindrum_murdnis on 2006-12-07
im guessing your using edgy first. I also installed this stuff here which may or may not be connected. im also guessing you had done what i ask you to do. If so try this wont hurt.

sudo login splash

sudo apt-get install gnome-splashscreen-manager

gksudo gdmsetup


Im not sure if system > preference > about me will give you the login pic...maybe

after you do all the above stuff re-do what i had asked above.

---

### Post by CatKiller on 2006-12-08
You can just put an image file called **.face** in your Home directory. There might be size/permissions/format constraints, but that's the gist of what the Login Photo application does for you.

---

### Post by Circus-Killer on 2006-12-08
> **Turner.kj said:**
> How does one change the login manager image? ](*,)   I have been to system->Preferences->Art Manger->Art->Other Themes->Login Manager and loaded the images, but I can not install.

open a terminal and type:

 $ sudo gdmsetup

---

