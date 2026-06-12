---
title: "I am a fool."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Sunships on 2007-05-15
Hello, I am using Xubuntu 6.10 (installed as Ubuntu, then converted). 

I read an earlier post about how Bum can be used to lighten the load on older laptops and thought I would try it too. I noticed GNOME as one of the options, and in my n00bish ways decided it was OK to disable this since I was using Xfce (or something like that!) - now when I start up the computer everything is text-based. I only know basic commands, so can't really get anything useful done anymore, and am writing this from another computer.

Does anyone know the command to bring back the desktop? Thank you very much! Apologies for foolishness!

---

### Post by Bachstelze on 2007-05-15
```
sudo apt-get install xubuntu-desktop
```

That should bring your Xubuntu back.

---

### Post by annda on 2007-05-15
have you tried 'startx' and 'startxfce' commands to start X/window manager?

---

### Post by Sunships on 2007-05-15
Hi HymnToLife, thanks for your advice. I tried it, and it replies to say that I already have the latest Xubuntu desktop - I guess I just need to re-enable it?

---

### Post by Sunships on 2007-05-15
> **annda said:**
> have you tried 'startx' and 'startxfce' commands to start X/window manager?

No - will give them a go.

---

### Post by Bachstelze on 2007-05-15
```
sudo /etc/init.d/gdm start
```

Try that too.

---

### Post by Sunships on 2007-05-15
Thanks annda and HymnToLife, startx did the trick! Now I can see what I'm doing again I should be OK :D

---

### Post by dasunst3r on 2007-05-15
+1 to annda's advice of using *startx* to get into your desktop.  From there, undo the change you made.  For future reference, *Gnome Display Manager (gdm)* is the thing that gets your desktop started, so it is important that you do not disable that.

P.S. You're not a fool.  We've all made silly mistakes like these... it's what happens when you take a leap of faith into something new.

---

