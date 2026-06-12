---
title: "Resolution too low... NEXT button is below screen margin"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Aymincendiary on 2007-08-08
I am setting up Ubuntu on a machine with a 17" monitor and onboard video. The problem I am having is the resolution is stuck at 800 x 600 and I can't set it any higher, AND the NEXT button is below the margin of the screen. Therefore I cannot install Ubuntu.

Can someone give me a keyboard shortcut to get around this limitation, or a way to increase the screen resolution to 1024 x 768?

Thanks!

Chris

---

### Post by igknighted on 2007-08-08
alt + click & drag will let you move the window around.

If you want to fix the res, open a terminal window (applications -> accessories -> terminal) and type "gksudo gedit /etc/X11/xorg.conf" (note, this is case sensitive).  Scroll down to a section called "screen" and there should be a place to add your resolutions there.  Save when you are done, then hit ctrl + alt + backspc to restart the graphics server and when it comes back your res should be fixed.

---

### Post by Inxsible on 2007-08-08
so you are still in the LiveCD right ?

have you tried changing the resolution. i think its in System --> Preferences --> "Resolution something or the other"

If you have already tried that, then you will need to modify the xorg.conf file.


Post the contents of the file here and someone will be able to help you further.
```
cat /etc/X11/xorg.conf
```

---

### Post by dargles on 2007-08-16
Hi, Folks.
I'm just picking up on this thread because I have a screen res problem - my LCD panel will take 1280x1024, but I'm only being offered up to 1024x768.  I've tried editing /etc/X11/xorg.conf, but it makes no difference.  In fact the file bears no relation to the resolutions I'm being offered.  Is it possible that it's *not* xorg.conf that I should be editing?  I'm using Feisty on one computer and Dapper Drake on the other.
Thanks, David

---

### Post by nickv777 on 2007-08-16
Hi  igknighted's,
Your method worked 1st time.

Thanx:)

---

