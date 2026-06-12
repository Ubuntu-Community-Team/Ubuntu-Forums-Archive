---
title: "Please help with a desktop problem!"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Rotaj on 2007-03-30
I have an empty desktop. no icons, no menus, no right-click context relative menus just the desktop image.
I had just installed a few themes though Synaptic and was playing around with them when all suddenly all screen edges went away. 

I am running Edgy(AMD64). 
Any suggestions for a quick fix?

---

### Post by acormack on 2007-03-30
Does a reboot fix  it?

---

### Post by Rotaj on 2007-03-30
The short answer is unfortunately, no

---

### Post by ardchoille42 on 2007-03-30
Nautilus manages the desktop icons, right click menu, etc. Try opening a terminal and running

```

nautilus

```If that brings the desktop stuff back, then you need to troubleshoot why nautilus no longer starts upon login as it should.
It's possible that a theme is interferring with the desktop.

---

### Post by acormack on 2007-03-30
if you type crtl+alt+1 does that allow you to log in at a text console

sudo useradd fred
sudo passwd fred

Then log in as fred

Do you have icons now?

---

### Post by Rotaj on 2007-03-30
Not at that system right now. I will try it when I get home. if that does not work and since I just installed last night I will just reinstall.
Thank You for the help.

---

### Post by fdrake on 2007-03-30
try to login in safe grafic mode or just login with the terminal safe mode and give us the content of the xsession-errors log file:
sudo nano .xsession-errors

---

