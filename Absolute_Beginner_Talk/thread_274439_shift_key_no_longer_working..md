---
title: "shift key no longer working."
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-10-09
my shift key no longer works, right or left, if i press it plus another button, nothing comes up.

---

### Post by meng on 2006-10-09
Weird problem. Have you got another keyboard you can try? Have you chosen a strange keyboard layout? (Sys > Pref > Keyboard) What if you run from terminal:
xev
Does it record the shift presses?

---

### Post by alex-desktop79 on 2006-10-09
yes it does, my layout is us

---

### Post by alex-desktop79 on 2006-10-09
is there a way to reset all my keys

---

### Post by qntgeek on 2006-10-10
I have the same problem. Randomly the shift key will decide not to work. If it happens while in locked screensaver I have switch users, log in as root and restart GDM to get it to reset the keyboard.

---

### Post by Paul41 on 2006-10-10
Try to go to Sys > Pref > Keyboard meng suggested and select a different keyboard model to see if that fixes it.

---

### Post by cookiemonster on 2006-11-08
I am also having trouble with my shift key.  I was running Dapper with no problem until a few weeks ago, when both shift keys stopped working.  The problem sort of came in and out, so I wasn't sure what was causing it.  I updated to Edgy and still had the problem, and just now I wiped my laptop and did a completely clean restall.  Still no shift key. This issue might force me to go back to Windows because I can't capitalize anything without the caps lock key and can't make symbols like parentheses or asterisks at all.  In the terminal, xev gives me no event for the shift keys although I am certain the keys themselves aren't broken.  I tried a few different keyboard layouts but no luck so far.  Any suggestions on how to get my computer to register the shift keys would be extremely welcome.  I'm currently running a new install of Edgy on an HP Omnibook XE3.  Thanks.

---

