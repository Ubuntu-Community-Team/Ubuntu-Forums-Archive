---
title: "Help: can't login to ubuntu!"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by Guest1234 on 2005-08-19
Hi I have installed sim(the icq client for linux), and when I try to close it, it refuses to quit.
so I killed the sim process, but it still left an "untitled window" in my panel, and wouldn't close. no matter what I did, I couldn't log out, I tried to kill the gnome-panel and revive it again but the "untitled window" stayed there, and wouldn't disappear.
So since I couldn't logout, the only option that I had left was to push the reset button.

Now when I starts the system with ubuntu(I have dual-boot), it says something
about 
```
Your session lasted less than 10 seconds, you haven't logout, try
login in one of the failsafe sessions and fix the problem
``` 

So now what I'm trying to do is logout from the shell(cuz I can't run the failsafe gnome session from some reason), but I don't know how to do it.

I tried "man logout", but it only directed me to a c function manual.
How do I logout from the shell?

---

### Post by jasmuz on 2005-08-20
Just type "exit"

But try this to see if you can login again, type rm .ICEauthority
exit from the console and try to do a graphical login again.

This mostly works :)

---

### Post by Guest1234 on 2005-08-20
Thanks a lot, it worked like charm!
What is this file anyway, and do I need it?
Cuz I searched for it and couldn't find it anymore.

---

### Post by jasmuz on 2005-08-21
Once you delete it, its created again, it serves as a reference poin for graphical logins under Gnome basicly.

---

