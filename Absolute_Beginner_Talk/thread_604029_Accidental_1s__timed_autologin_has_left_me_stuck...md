---
title: "Accidental 1s  timed autologin has left me stuck..."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by barkerben on 2007-11-05
Hello,
I have just installed Ubuntu 7.10, and have done something rather silly. Accidentally I set the timed login to 1 second, but the login details are incorrect, so as soon as gdm loads, I get an "invalid credentials" box, which reappears as soon as I cancel... 

How can I change the settings back to something more sensible, when it is continually trying to log me in using an invalid password? I can boot into the recovery console, so I assume I could do something here...not sure what though :-p


Cheers,

Ben

---

### Post by daimaru on 2007-11-05
to get back to login screen hit ctrl+alt+backspace then enter right credentials. once logged in go to system->adminstration-> users and groups and change your password , or just turn off auto login.
and if you never get to graphical login hit ctrl+alt+f1 log in with your username and password then type 
```
passwd
```
type in your old password and then the new one you want to use. hmm don't really know if that is what you wanted to know but if not post again and explain.

---

