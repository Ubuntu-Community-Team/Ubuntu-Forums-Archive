---
title: "Stupid gray panel"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by stk47rr on 2007-02-10
below is a screenshot of my desktop. i've tried everything to get this gray panel off and i can't.

also, i want to install compiz.when i try to access my source list i get permission denied. so i installed it using syn pack manager. when i type compiz in the terminal i get this

stk47rr@stk47rr-laptop:~$ compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No manageable screens found on display :0.0

please help. i used to have beryl but i restared my computer one day and it wouldn't start because there was a problem. i couldnt remember the problem to i reinstalled ubuntu and tried to install beryl again and the same problem happened again so i'm staying away from beryl. i also heard compiz is more stable.

---

### Post by nickoli_02 on 2007-02-10
That grey panel is the taskbar, I believe. It looks like whatever theme/window manager you're using is only half-done.

You need to edit the sources.list file as root. To do so, type

```
sudo gedit /etc/apt/sources.list
```

in the terminal. 

The error you're getting is because you can only use one window manager at one time (beryl and compiz are window managers). To do so you'll have to tell gnome or whatever you're using to use compiz. Not quite sure how to do this, look for a compiz how-to.

---

### Post by ComplexNumber on 2007-02-10
> **stk47rr said:**
> below is a screenshot of my desktop. i've tried everything to get this gray panel off and i can't.


its because you're using mac os x style taskbar(?). i can't remember exactly where exactly it is in the kde control centre that you change it (i'm not running kde at the moment), but i think it could be in 'desktop -> panel' or 'desktop -> taskbar'. you could do a search for "mac".
to get to the kde control centre, fire up the terminal and type in kcontrol.

---

