---
title: "extending the gnome menu bar across two monitors and shift+backspace restars X"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Alex6969 on 2006-12-08
I'm running dual monitors and i would like the main gnome menu bar to extend across both monitors, so that it is one contiunous bar, not two seperate ones (like windows).

also when ever i hit backspace and shift at the same time it restarts X, witch is very anoying when you lose your recent work on a college essay. is there a way to fix this little problem?

---

### Post by jpkotta on 2006-12-09
Shift-Backspace: [http://ubuntuforums.org/showthread.php?t=280872](http://ubuntuforums.org/showthread.php?t=280872)

I don't know about the panel.  Are you running 2 different X servers or just one that spans 2 screens?

---

### Post by Alex6969 on 2006-12-09
just one that spans both screens would it be better to run two different ones?

---

### Post by jpkotta on 2006-12-09
I would think that just one is the way to go, but I've never ran dual monitors before so I can't say for sure.  If it is relatively easy to set it up the other way, try it; otherwise I wouldn't bother.

If windows can be partially in both screens at once, I would think there is a way to have a panel occupying both screens at once.

---

### Post by Alex6969 on 2006-12-09
how would i go about setting up each display to use its own xserver?

Would that fix my problem?

---

### Post by jpkotta on 2006-12-09
The "one" in my previous post refers to a single X server controlling both screens.

---

### Post by Alex6969 on 2006-12-10
thats what i was talking about also, running two x servers, one per monitor

---

### Post by bodhi.zazen on 2006-12-10
> **Alex6969 said:**
> how would i go about setting up each display to use its own xserver?

Would that fix my problem?

This is how I do it:
[Dual monitor](http://ubuntuforums.org/showthread.php?&t=240150)

Set up your xorg.conf

Then:```
sudo /etc/init.d/gdm stop
/usr/bin/startx /usr/bin/gnome-session -layout DUAL
```

---

