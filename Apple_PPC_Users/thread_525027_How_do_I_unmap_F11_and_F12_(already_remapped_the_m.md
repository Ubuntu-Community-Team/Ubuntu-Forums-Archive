---
title: "How do I unmap F11 and F12? (already remapped the mouse buttons)"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by paulsomm on 2007-08-13
Forgive me if this is answered but I can't seem to find a workable answer.

I already edited my sysctl.conf file and remapped my right mouse and left mouse buttons to fn+alt and fn+apple keys and am quite happy.

The problem I realized after running this way for awhile is when I use an app that requires F11 or F12, they still seem to activate the middle and mouse buttons.

Yes, I've restarted after changing my sysctl.conf.

Is there somewhere else that these keys are specified?  An X11 conf file perhaps?

Thanks in advance :-D

---

### Post by thevictor390 on 2007-08-14
Same problem here.  I commented out the mappings for F11 and F12, changing them to apple and fn+apple (supposedly, I followed a tutorial).  But now F11 and F12 still are mouse buttons not function keys.  Not my biggest problem right now but would be one step closer to getting this thing complete.

---

### Post by paulsomm on 2007-08-15
Ah, well at least I don't feel crazy anymore ;-)

I ran a grep -r against my /etc folder for the keycodes for F11 as well as the words "F11" and "f11" but found nothing of note.

---

### Post by tonyr on 2007-08-17
Uninstall the **mouseemu** package.  You can do it from Synaptic, or in a terminal with
```
sudo apt-get remove mouseemu
```
The **mouseemu** package is installed by default.  

I had to do this to get the Eject key on the keyboard to act like an Eject key should.  I had to 
redefine the Eject key in Keyboard Shortcuts to be F12 instead of the default **0xcc**, too.
What the heck is **0xcc**, anyway?


- tony

---

### Post by thevictor390 on 2007-08-17
Thanks, I'll try that out.

---

### Post by paulsomm on 2007-08-22
Ah Tonyr you are the man :)

Thanks for that tip!

---

