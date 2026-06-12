---
title: "Reinstall Ubuntu with no CD????"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by FAMUgolfer on 2008-02-11
Can I renistall Ubuntu without the CD??

When i turn my computer on it sets up normally with login and password.  But after I enter my login and password it just goes into a blank tan screen. 

PLEASE HELP....I'm a noob.  I think i'm missing some evolution files and tried recovering them from the terminal ("select session"-->failsafe terminal------>synaptic) but couldn't recover all the missing files.

---

### Post by Joeb454 on 2008-02-11
Broken Evolution files shouldn't affect your login.

How long have you left it on the tan colored screen?

---

### Post by jan quark on 2008-02-11
if the failsafe session works

try to reinstall

ubuntu-desktop

via synaptic

just a guess because I do not know what do you have done to your machine :)

---

### Post by FAMUgolfer on 2008-02-11
thank you for your responses

i was able to find ubuntu-desktop via synaptic but some of the files were not able to be "fetched" 

Is there something wrong with my repositories

ive already tried apt-get update and also tried to apt-get install evoltion but it doesn't seem complete

i'm also trying to burn the cd but that seems like it keeps burning the image and not all the files.

---

### Post by amingv on 2008-02-11
Try :
```
sudo apt-get install ubuntu-desktop --reinstall
```

---

