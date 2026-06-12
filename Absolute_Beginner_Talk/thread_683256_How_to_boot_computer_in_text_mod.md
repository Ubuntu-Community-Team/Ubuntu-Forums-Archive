---
title: "How to boot computer in text mod?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by suweihsut on 2008-01-30
I run my computer in ubuntu 7.10 and I want to boot the computer in text mod. But I don't know how to do it. Thank you.:)

---

### Post by jordanmthomas on 2008-01-30
```
sudo update-rc.d -f gdm remove
```
If you run this, gdm will not automatically run on boot.

---

### Post by x1a4 on 2008-01-30
Hi,

Rename the file /etc/rc2.d/S30gdm to /etc/rc2.d/K70gdm like so: 
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm
```

---

### Post by suweihsut on 2008-01-30
Then I can run "startx" to run "gdm", is it that right?

---

### Post by oedha on 2008-01-30
yup...you're right
~E~

---

### Post by jordanmthomas on 2008-01-30
Not exactly, if you run startx, the contents of 
```
~/.xinitrc
``` will be run.  A quick, simple one that will start gnome is this:
```
#!/bin/sh
exec gnome-session
```
If you don't have a .xinitrc file I'm not sure what exactly will be run.

To run gdm after disabling it, you'll want to run
```
sudo /etc/init.d/gdm start
```

---

### Post by suweihsut on 2008-01-30
Yeah, I get it. The important thing is that gdm don't run in boot time. Thank you everyone.:)

---

