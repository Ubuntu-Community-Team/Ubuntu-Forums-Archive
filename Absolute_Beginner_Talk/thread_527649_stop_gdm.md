---
title: "stop gdm"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by serfczar on 2007-08-16
How do I stop or uninstall gdm once i've installed it?

---

### Post by aysiu on 2007-08-16
```
sudo /etc/init.d/gdm stop
sudo apt-get remove gdm
```

---

### Post by serfczar on 2007-08-16
Ok, I got that, and now my vnc won't work, what vnc will work without gnome?

---

### Post by aysiu on 2007-08-16
GDM shouldn't affect VNC.

You will, however, need a graphical interface of *some* kind. And you should still be able to log into Gnome after having removed GDM. Gnome and GDM are **not** the same thing. GDM controls the login screen. Gnome is what happens *after* you log in.

---

### Post by serfczar on 2007-08-17
so if i remove the login screen, what user will I be?

---

### Post by aysiu on 2007-08-17
Well, if you remove the login screen, you'll boot to a command prompt (which is a text-only login screen). So there's no default username. You still log in, just not graphically. You can then reach Gnome by typing ```
startx
``` after you log in.

---

### Post by az on 2007-08-17
What exactly do you want to do?

---

### Post by serfczar on 2007-08-17
> **az said:**
> What exactly do you want to do?

Just learning here, I'm an ubuntu n00b.

---

### Post by soniagulrajani on 2007-11-17
Hi,

I am facing some problems when i give the following command:

sudo /etc/init.d/gdm stop

I do not get the command prompt after this. I do get rid of the GUI, but I can't proceed because I don't have a command prompt. 

I have some other questions too:

1. I am running 3 Vmware workstations with Ubuntu as the Guest OS. I can't allocate more than 100 MB RAM memory for each one of them(recommended is 256 MB).Will turning off gdm help in this case? or do I need to turn off the XServer too?

2. With GUI enabled, I can have multiple terminals. Is there a way I can have more than one terminal/console with GUI turned off?

Any help will be appreciated.

Thanks,
Sonia

---

