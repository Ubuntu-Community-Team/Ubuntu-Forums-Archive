---
title: "Weird problem - gutsy - text entry on web pages"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by EAL on 2007-10-20
This is a weird one.  Everywhere I enter text on a web site, the performance slows down dramatically.  This happens on this forum, other forums with different forum software, gmail - seems like anywhere you enter text.  Everything else is fine.  To write this post, I composed it in gedit and copy/pasted it here.  Otherwise, its type a sentence, then watch it appear at the rate of about one letter per second on the form.  

While I'm trying to type something, other things seem to slow down too - like the applications menu, etc.

I installed (updated to) 7.10 last night.  It took some doing to get the eye candy working - I followed the steps I found here:

> First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


[http://ubuntuforums.org/showthread.php?t=576624](http://ubuntuforums.org/showthread.php?t=576624)

Since I've noticed the problems, I've disabled the effects in Preferences>Appearance but that doesn't help.

---

### Post by EAL on 2007-10-20
Update:

This seems to be a problem with Firefox.  Opera works normally, but I don't want to use Opera.  :)

Changing the xorg.conf back to the way it was didn't solve the problem.

---

