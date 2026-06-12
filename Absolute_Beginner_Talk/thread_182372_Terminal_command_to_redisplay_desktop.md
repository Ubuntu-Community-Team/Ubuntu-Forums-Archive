---
title: "Terminal command to redisplay desktop?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Ken Burgard on 2006-05-25
I have installed Gcompris (kid-games suite) but it causes my screen to go black.  CTR+ALT++(-) does not fix problem.  What command, in Terminal (ctr+alt+f1) will get my desktop back up?  What command will shut down operating system if desktop won't come up?  I've been forced to power down the computer to get anywhere.

---

### Post by Sef on 2006-05-25
Have you tried ctrl + alt +F7?

---

### Post by Ken Burgard on 2006-05-25
sorry, forgot to say I run Breezy Badger 5.10.  And I have tried F everything.  That may have been the key that brought up a list of things I did not know what to do with.

---

### Post by confused57 on 2006-05-25
This link may help:

[http://www.er.uqam.ca/nobel/r10735/unixcomm.html](http://www.er.uqam.ca/nobel/r10735/unixcomm.html)

---

### Post by Ken Burgard on 2006-05-26
Thank you, I bookmarked that page.  Will have to study it thouroughly as I still don't have my printer working!! (Can't print a cheat sheet)

---

### Post by confused57 on 2006-05-26
I hoped that link would give plenty of F things to try, you may also want to try after doing Ctrl+Alt+F1:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

---

### Post by joshrobinson on 2006-05-26
[QUOTE=confused57]I hoped that link would give plenty of F things to try, you may also want to try after doing Ctrl+Alt+F1:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start[/QUOTE]

i was just about to post that when i saw this thread.. ](*,) :twisted:   :-D

you can also use startx instead of gdm start

---

### Post by Ken Burgard on 2006-05-27
[QUOTE=Sef]Have you tried ctrl + alt +F7?[/QUOTE]

What finally worked was CTR+ ALT +F1 THEN 'Log in' THEN CTR +ALT+ F7 THEN CTR +ALT+ BKSP .  This take me back to the Unbunto sign in page.  There may be a better way but this has allowed me to not power down the CPU.

---

