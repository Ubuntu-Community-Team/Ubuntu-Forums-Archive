---
title: "Can't restart from Gnome?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by fishy on 2005-11-29
After recently installing the nvidia drivers on my system, I am no longer able to restart from System -> Log Out -> Restart the computer. This command shuts down the X server and kicks me out to a command prompt. However, System -> Log Out -> Log Out and System -> Log Out -> Shut down still work just fine. Also, CTRL + ALT + Backspace used to restart the X server (before nvidia driver installation) but now it also just shuts down the X server and leaves me at the prompt. Can anyone help me get things back to the way they were?
Thanks

---

### Post by goodmanbrown on 2005-11-30
This is just a guess, as I'm not at all sure what your problem really is.  But it sounds like GDM is crashing when your X server is killed.  I think the first thing I would try is just reconfiguring GDM.

```
sudo dpkg-reconfigure gdm
```

You could also try what probably amounts, in this case, to the same thing:

```
sudo apt-get install --reinstall gdm
```

---

### Post by fishy on 2005-11-30
Brilliant! That seems to have done the trick.
Thanks again

---

