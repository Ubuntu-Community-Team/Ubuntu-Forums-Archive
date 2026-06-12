---
title: "[SOLVED] How Do I Stop VNC Server From Automatically Starting?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-18
I have a program running in Session Manager called vino-session.  When I did some digging to see what it is, I find that it is the VNC Server for Gnome.  I have no need for a VNC Server, and I would like to know how I can disable it from auto running every time Gutsy starts up.  

I figure the less resources running, the more memory I'll have for other system tasks, right?

---

### Post by oedha on 2008-03-18
have you check on system - preferences - session ?

---

### Post by FreewareFan on 2008-03-18
> **oedha said:**
> have you check on system - preferences - session ?

Yep.  That's the name of the program that runs, when you select system - preferences - session...  Session Manager.   That's what showed me that vino-session was running.   But, vino is not in the autostart tab section for me to disable it's being started automatically.

Thus my question, how do I stop it from being run, because I really don't need or want it running.

Thanks.

---

### Post by FreewareFan on 2008-03-18
OK, I got it.  For anyone else who doesn't want the VNC Server running needlessly, here is what you need to do:

How to disable vino-session: open /usr/share/gnome/default.session

Then  change the value of num_clients from 6 to 5 

Comment out the last three lines starting with 5.

Save, and re-boot.

That did the job for me, and I now have one less thing running in the background that I don't need or want.

FwF

---

