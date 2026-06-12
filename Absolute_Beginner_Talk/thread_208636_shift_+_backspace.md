---
title: "shift + backspace"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by kigina on 2006-07-03
how do i disable it from logging me out

---

### Post by kigina on 2006-07-03
plz answer

---

### Post by kigina on 2006-07-03
PLEASE
this little "feature" is what is probably keeping from ditching windows
i cant even design my websites with out losing everything and accidently logging out

---

### Post by T700 on 2006-07-03
Do you think begging will make people answer more quickly?  You only posted your orginal question 30 minutes ago and you've demanded twice more that someone help you!

Personally, I'd suggest you just learn to stop hitting that particular combination of keys, but failing that, try the xmodmap command.

Paul

---

### Post by kigina on 2006-07-03
im just getting really annoyed with it
im sure you know how long typing up a php page takes

---

### Post by Dandroid on 2006-07-08
I am very familiar with your frustration and pain but I did find a fix for the problem.  

The following command will fix the issue.
```
xmodmap -e "keycode 22 = BackSpace"
```

I installed XGL using poofy's guide that involves running the file 'thefuture'.

If you have this file set to run on startup then just add that command onto the end of it.  Mine looks like this:
```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap -e "keycode 22 = BackSpace"
```

Good luck!

---

### Post by daschl on 2006-08-21
> **Dandroid said:**
> I am very familiar with your frustration and pain but I did find a fix for the problem.  

The following command will fix the issue.
```
xmodmap -e "keycode 22 = BackSpace"
```

I installed XGL using poofy's guide that involves running the file 'thefuture'.

If you have this file set to run on startup then just add that command onto the end of it.  Mine looks like this:
```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap -e "keycode 22 = BackSpace"
```

Good luck!
wow thanks it works for me too! it's really annoying

---

### Post by got_nix on 2006-09-22
and in the event that your not running the file the future you should be able to set that to run in the session startup for gnome right?

---

### Post by Jeremiah478 on 2006-10-19
Just wanted to say thanks for the fix, I added:
xmodmap -e "keycode 22 = BackSpace"
to the startup and I'm no longer plagued by the shift+backspace combination

---

### Post by billygates on 2007-03-29
I finally got it to work!!!!

Adding "xmodmap -e "keycode 22 = BackSpace"" to start up made it go away.

Thank you.  Thank you SO much.

---

