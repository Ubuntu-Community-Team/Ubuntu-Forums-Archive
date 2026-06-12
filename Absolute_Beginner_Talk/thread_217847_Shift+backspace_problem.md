---
title: "Shift+backspace problem"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-17
My keyboard's shift key tends to get stuck & when I press backspace it actually logs out & its extremely annoying! How do I change this?

---

### Post by Thenotsowyzewun on 2006-07-17
Click System, Preferences, Key Combinations, it's the 2nd one on the list :).

---

### Post by kris2pe on 2006-07-17
Do you mean Keyboard shorcuts? Coz logout shorcut is disabled odd enough!

---

### Post by Thenotsowyzewun on 2006-07-17
Oops my bad.

Add this to startup:

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
``` 

To do that browse toSystem, Preferences, Sessions, Startup programs, btw :).

---

### Post by kris2pe on 2006-07-17
The code didn't it still does the same thing
I hope this screenshot helps 
[IMG]http://img81.imageshack.us/img81/8554/screenshothl3.png[/IMG]

---

### Post by woedend on 2006-07-17
LOL
its an XGL problem that kills the xserver.  This command will fix it.

setxkbmap -model pc105 -layout us -variant basic


for american keyboards, if you are in britain replace us with gb...so on and so on.  
it needs to be run everytime you restart..
Oh, and to make it easier, if you use a script to automatically start compiz(like thefuture on here)...just add that line to the end and save it so that it will be run automatically.

---

### Post by kris2pe on 2006-07-17
Can I put this in sesssions? 
How do I put this in the xgl's script! Noobie here!!!

---

### Post by woedend on 2006-07-17
don't put it in xgl script, put it in compiz script.  How do you run compiz?

---

### Post by Thenotsowyzewun on 2006-07-17
Yeah add it to Sessions.
I'm abit of a noob sometimes too, didn't know how to run a sh installer yesterday (I've recently returned to *nix after a very long hiatus!).

---

### Post by woedend on 2006-07-17
Seeing as the only time you would ever want or need to run it is when using compiz, I would add it to the COMPIZ script instead of using sessions.
Youll find out also that when you start adding and deleting users who want to use compiz as well that its easier this way.

---

### Post by kris2pe on 2006-07-17
I just follow instructions aimlessly! I used the compiz-start.py
which is python script & I have deleted the original file & I don't where it is now! 
But the compiz thing still works! :) 
anyways your input will b greatly appreciated :)!!!

---

### Post by woedend on 2006-07-17
read poofyhairguys compiz/xgl post.  He has you make a file called /usr/bin/thefuture
instead of a python script.  Use his but DO NOT use the xmodmap part, use the part I wrote above.  It works better.

---

