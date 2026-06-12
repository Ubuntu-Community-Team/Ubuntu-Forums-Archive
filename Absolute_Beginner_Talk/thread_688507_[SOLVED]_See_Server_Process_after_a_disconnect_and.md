---
title: "[SOLVED] See Server Process after a disconnect and reconnect"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2008-02-05
Hey,

So I setup a server in my house and I can remotely connect to it using ssh. And I started installing Steam Dedicated sever on it. Since it takes a while, does anyone know how after I disconnect from the server, I can view the progress of the install?

Even if its a system upgrade, does anyone know how I can view the progress/output after I have closed the terminal?

---

### Post by AegisTalons on 2008-02-06
So during my TA session, one of the students showed me that there is a program called "screen" which is a handy little program. Effectively, what it does is it saves different screens similar to different desktops on GUI. 

If you are connected to a server, and tell the server to upgrade its software, if you disconnect it will immediately stop the process. If you save it to a screen, it runs it in the background. You can then later recall the screen.

screen -S "Screen Name" : creates a terminal for a process you want to run later
[Ctrl] +A D : detaches current screen
screen -R : Resumes detached screens

---

