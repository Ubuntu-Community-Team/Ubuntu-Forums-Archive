---
title: "Vnc ?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by cytg on 2007-06-26
Perhaps someone will have experienced this before me.

i have enabled remote desktop and i can connect fine.

However it wont update the screen when i perform an action .. well maybe draw a line, a few pixels, thats it... if i want to see the results of my actions, i have to log in again.

I used to do this to my windows box(same box actually) from this same location with little to no problems, and the setup is the same ( i have tried different clients just now, just to eliminate the possibility)

Any ideas welcome :)


Oh yea, im impressed by ubuntu this far, i may not have to go vista after all ...

---

### Post by cytg on 2007-06-26
hilfe ?

---

### Post by lazyart on 2007-06-26
sounds like you have desktop effects/beryl running which makes this problem crop up.

1- disable desktop sharing
2- install x11vnc from synaptic (or sudo apt-get install x11vnc)
3- run it via x11vnc -noxdamage -forever -passwd *password*
(password is an optional field)

and you should be able to connect.  You'll want to add that as a startup program-- enter the same line as a startup command (system>preferences>sessions)

---

### Post by cytg on 2007-06-26
Thats excatly true ... ill give that a go when i get home .. thanks!!!

---

### Post by cytg on 2007-06-27
while i could connect once like this, i cannot a second time ... client connects allright, negotiates protocol with server, waiting for some server-message and then .. nothing... argh

---

### Post by xl_cheese on 2007-06-27
I'm having the exact same issue.  Thanks for the solution.  I'll have to try it when I get home.

---

