---
title: "Auto-login two sessions"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by slink on 2007-09-25
Hi, 

I wish ubuntu to automatically login onto 2 sessions on startup.

I can set it to automatically login 1 session  

( [FONT="Courier New"]System-->Administration-->Login Window
Security-->Enable Automatic Login[/FONT] ) 

**_OR_** to automatically login after a short delay, but...


can't I make it automatically login one session **_AND_** then automatically login another session ?

Maybe there are multiple possible answers to issue...

---

### Post by justleen on 2007-09-25
you want to start to X sessions at start up, and autologin to that?

or you want to users logged in, so you are able to switch?

---

### Post by slink on 2007-09-25
I want my machine to autologin to 2 users at startup.

---

### Post by Sturmeh on 2007-10-14
I also just learn't how to autologin, but how would i go about forcing the screensaver the second it logs in?

---

### Post by CheShA on 2007-11-29
[Bump!] I've also wanted this answered [for a while]("http://ubuntuforums.org/showthread.php?t=547851&highlight=multiple+auto+login").  I've found vague info on how to do it [one way for some distros]("http://www.linuxquestions.org/questions/linux-desktop-74/multiple-autologins-multiple-users-multiple-sessions-587056/") and also an official open request for a patch for gnome to allow this easily, but no one has been able to answe how it might get done under Ubuntu.

This is doing me in, It's te one thing I've really *needed*  for several years, both under Windows and Linux.  I'd like to auto log in My session, my girlfreinds session and a public session to my main PC and be able to switch between them all easily.

Does anyone have any thoughts?

---

### Post by CheShA on 2007-11-29
FWIW what I currently have is that on boot, my PC auto logs in as my girlfriend (System> Administration>Login Window> Security > Auto login the following user), Then as one of her startup items I run ```
gdmflexiserver
```.  This basically gives me a 1 second flash of a beige desktop before presenting the login screen.  I end up only having to log in once to access my login session and hers is already running. I want to be able to do this to the public account as well though.

---

### Post by Partyboi2 on 2007-11-29
> **Sturmeh said:**
> I also just learn't how to autologin, but how would i go about forcing the screensaver the second it logs in?

Add this to Sessions (System>Preferences>Sessions)
```
gnome-screensaver-command --lock
```

---

### Post by slink on 2007-11-30
The closest trick I ever found was:

[http://ubuntuforums.org/showpost.php?p=3392113&postcount=10](http://ubuntuforums.org/showpost.php?p=3392113&postcount=10)

---

