---
title: "hangs at startup"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by khoda on 2006-07-21
First day linux user...

I just installed Ubuntu, then did a
apt-get install ubuntu-desktop

I did this, and it finished and led me to a black screen after it got 100% and unpacked. 

I rebooted, and I type in username/password then it gets to the ubuntu logo (looks like a splash logo) and it hangs there. The logo looks messed up (like it needs my gfx drivers).

what do i do now? it doesnt go to console, it goes straight to gnome.

---

### Post by lamego on 2006-07-21
You can switch to console with "CTRL-ALT-F1".
The reconfigure the X server type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Saphira on 2006-07-21
At this point you might need to reinstall. Your early into it, but after installing you dont really need to do a apt-get install ubuntu-desktop. That is unless you installed from a kubuntu or xubuntu CD and your wanting to get gnome instead of KDE or XFCE.

---

