---
title: "Problem after install"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by cjh210359 on 2006-05-13
Hi,
I've installed ubuntu, but when I boot up, I login to a command line, not a GUI.  Is the installation of GNOME a separate step?  What am I missing

---

### Post by Iarwain ben-adar on 2006-05-13
Hi,
well, did you install the "server" or the "desktop" version? (server doesn't come with DE)

If you installed server => sudo apt-get install ubuntu-desktop
if you installed desktop => X 


Iarwain

---

### Post by cjh210359 on 2006-05-13
desktop

---

### Post by Iarwain ben-adar on 2006-05-13
Do you get any errors when booted up? (why X couldn't be started etc...)

If you don't, type
> X

and that should start the X-server


Iarwain

---

### Post by cjh210359 on 2006-05-13
Iarwain,

I must have had some errors along the way (I wasn't watching the install closely).  I'll try it again.

Thanks for your help.

Chris

---

### Post by Iarwain ben-adar on 2006-05-13
No problem,
if you have anymore questions, post them here :-)


Cheers,


Iarwain

---

