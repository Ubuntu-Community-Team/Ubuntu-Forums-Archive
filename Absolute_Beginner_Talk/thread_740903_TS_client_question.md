---
title: "TS client question"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-03-31
Trying to go fullscreen with tsclient, 

What is the switch?  If I enable alternate switch it errors out.
Want to be able to switch from full screen tsclient to full screen ubuntu.

Thanks

---

### Post by dstew on 2008-04-01
Looks like a bug. The TSclient front end seems to be sending the rdesktop back end the invalid switch -F. The switch should be -f.

Anyway, uncheck the full-screen alternate box and try the ctrl-alt-enter key combination. This is advertised as causing full-screen switching. See the [rdesktop man page]("http://linux.die.net/man/1/rdesktop").

---

### Post by firedrow on 2008-04-01
I always use "Operate in Fullscreen Mode" and have the "Alternate Fullscreen Mode -F" unchecked.  It has always worked for me.  Then use Ctrl+Alt+Enter when I need out of fullscreen.

---

### Post by TechDragon on 2008-04-02
yes, that was what I was looking for 

THANK YOU!

---

