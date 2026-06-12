---
title: "Opera conflicts with Opera?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by 141N on 2007-04-05
Hey guys, I took some previous advice with Firefox crashing on me all the time and went to install Opera, so I did
```
sudo aptitude install opera
```
And was told that there was, something to the effect of, Error: Opera conflicts with previous installation of Opera - theres a hidden directory .opera

Anyway, i removed that and downloaded the file from Opera's homepage and installed it with the GUI but same thing again :( 

Can anyone help, I really wanna get going with Ubuntu but this is a major setback not being able to get online for any decent length of time

---

### Post by kahrytan on 2007-04-05
Did you try uninstalling the old Opera from with Synaptic? Then install new the package?


/home/username/.opera folder is where your settings and cache was.

---

### Post by eljalill on 2007-04-05
You might want to see in synaptic, whether you have anything a category "Not installed (residual config)" or "auto removable" on the left. If there is some opera package in there, that might not let you install...

Else you could try "locate opera" if you are sure, that you actually uninstalled the program, because not only your user, root and other users also have .config files.

---

### Post by 141N on 2007-04-05
Ah, that might be the problem - kahrytan: I removed it in Synaptic as well, or I had a look in Synaptic after removing it in the terminal can't remember right, but as eljalill suggested I didn't do it for any other users or anything - but then again, I am the only use on it so then surely the only filepath would be /home/iain/.opera ?

---

### Post by eljalill on 2007-04-05
As far as I know, you always have also root as a user... unless you did sth to it.
try 
```
locate opera 
``` to see, whether there are any config files remaining...
My root also has an opera config file  in /root.

---

### Post by 141N on 2007-04-05
Hey, sorry took so long to reply back - I'll try that tonight thanks, hopefuly that'll stop it crashing on me all the time :) I'll post back here if it makes any difference

I wasn't aware Ubuntu let you log in as the root user - I'm sure I read/heard that somewhere, is that right?

---

### Post by eljalill on 2007-04-05
```
sudo su
``` changes you to be root in the terminal. (and you'll be in root's home, not your home)
You can also enable the root acount, and you can login with the login screen... but I personally don't think you need that. (But you'll find Howtos in the forums, I am sure)

However, the root account/user still exists, even if you can't log in with it on the login screen.

If I am not mistaken that is actually also what sudo does, it lets you execute a command as root (or any other user), so it's like a short time log in to the root account.

---

### Post by 141N on 2007-04-05
yeah, i knew sudo was something like that (I assumed it was Super-User-Do [command]) or something like that lol - urban myth or somethin along those lines :P thanks for your help

---

