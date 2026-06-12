---
title: "Boot screen never shows up"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Drittponken on 2008-03-22
Hi.

I just finished installing Ubuntu on my "new" laptop.
But there is one thing that annoys me.

When i select to boot Ubuntu in grub, i should get a progress bar (like in XP) that shows the progress of loading Ubuntu. 

But i get nothing, instead i get a completely black screen for a long time (too long) and then the login screen. 


Why? I have never had this problem before, i'm running Gutsy Gibbon

---

### Post by scragar on 2008-03-22
```
sudo apt-get install startupmanager
sudo startupmanager
```
and look under the second tab for usplash themes

---

### Post by dankdank on 2008-03-22
try this

open up terminal and type

sudo gedit /etc/usplash.conf

type in you PW

then you should get something like this

# Usplash configuration file
xres=1280
yres=800

make sure the bottom number is 800

that should fix it

---

### Post by skrimpy on 2008-03-22
[http://ubuntuforums.org/showthread.php?t=317888](http://ubuntuforums.org/showthread.php?t=317888) 

I found that thread to be useful, post 5 especially :) HTH

---

### Post by Drittponken on 2008-03-22
Thank you guys. I'm gonna check into your answers. 
I really appreciate the fast answers.:)

---

### Post by tomtrauberts on 2008-03-22
> **dankdank said:**
> try this

```

sudo gedit /etc/usplash.conf

```

# Usplash configuration file
xres=1280
yres=800

make sure the bottom number is 800


I'm using a Dell Inspiron E1505 laptop, and this got my splash screen to show up on shutdown, but not on startup.

For startup, I had to use startup-manager (sudo apt-get install startupmanager) and change the boot display from 640x480 to 1024x768.

---

### Post by Drittponken on 2008-03-24
> **tomtrauberts said:**
> I'm using a Dell Inspiron E1505 laptop, and this got my splash screen to show up on shutdown, but not on startup.

For startup, I had to use startup-manager (sudo apt-get install startupmanager) and change the boot display from 640x480 to 1024x768.

Same here. but it worked so big thanks :)

---

