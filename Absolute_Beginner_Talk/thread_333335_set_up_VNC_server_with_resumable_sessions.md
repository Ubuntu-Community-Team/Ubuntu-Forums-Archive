---
title: "set up VNC server with resumable sessions"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by mike_plays_golf on 2007-01-07
I have read through several of the postings and found them quite helpful as I am new to Linux (going on 8 hours) and am still translating windows to Linux versus thinking in Linux.
As I have been trying to get things I think I need to work going, I have been reading about VNC servers on Linux.  I use these quite a bit at home and work to be able to log on to a computer and do things.
I have VNC server up and running on this installation of Ubuntu 6.06.1 but it just allows me to log in again or as another user.
Can I take over a "session" or screen of an all ready logged in user (i.e., I start a process and want to see how it is going without walking over to the computer).
Again, all the other postings and answers have been extremely helpful to this point, Thanks!

---

### Post by Scorpuk on 2007-01-07
Try connecting to your ip with :0 at the end.


ie

your server is on 192.168.1.1 (or whatever)

connect on 192.168.1.1:0


I do this to connect to my box and take over the auto logged in user (me).


There maybe some options you need to set up, but I cant remember where they are (as I am not at home), but you might want to uncheck the option where the current user has to click ok to accept the control through vnc and maybe add a password too.

---

### Post by mike_plays_golf on 2007-01-07
Scorpuk, I tried the :0 when trying to login from my Windows machine and it gives me the "connection refused (10061)" message.
Thanks for the thought, any more would be apprectiated!

---

