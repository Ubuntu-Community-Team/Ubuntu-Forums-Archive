---
title: "Ubuntu keyboard problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2008-02-16
Hi! I'm on a MacBook,

I've installed Ubuntu and everything went fine but I have the keys "<" and "º" exchanged. I mean if I want to type "<" I must press "º" and the reverse way.

Anyone knows how I could change that back?


Thanks again!

---

### Post by The Hunt For Ida Wave on 2008-02-16
Have you tried changing your keymap? Go to applications>other>keyboard layout. 
Make sure the active keymap selected is the appropriate one. Hope that helps.

---

### Post by fredscripts on 2008-02-16
Thanks for aswering.Yes, in fact the only key I'm having problems is that one. The rest work perfectly.

Any ideas ?

---

### Post by The Hunt For Ida Wave on 2008-02-16
The only thing I can suggest then is going back to the Keyboard Layout options, remove every single active layout, apply the change, then add the appropriate layout again, then apply again. That worked for me when my keyboard kept reverting back to the US keymap, even though GB was the only active one.

---

### Post by Pelham123 on 2008-02-16
Or...

There is always xev and xmodmap for manually changing keymaps. Heres a couple of links I found; first one explains xev as well, the second link is just the 'man' page of xmodmap with a few examples (but one of the examples is about swapping keys). Good luck if you use these....thought my brain was going to prolapse

[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

[http://www.xfree86.org/4.2.0/xmodmap.1.html](http://www.xfree86.org/4.2.0/xmodmap.1.html)

;)

---

