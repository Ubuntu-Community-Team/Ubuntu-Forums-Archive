---
title: "[SOLVED] desk top goes black then back to login screen??"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-03-01
ok this is the second time this happened, working with ubuntu 7.10,first time left computer on came back about 4 hours to a black screen, the monitor had a green lite to connection was ok , could not do anything but power of and then re start, second tine just a few minutes ago working on line and playing music, screen black hit enter took me to the log on screen, had to reenter my user name and password,

any ideas as what is causing this??

---

### Post by jan quark on 2008-03-01
have a look into the system logs

system > administration > system logs

anything suspicious messages just before the black screen?

---

### Post by broekskw on 2008-03-01
thanks jan quark, here is a screen shot , not to sure what this all means
also my firefox keep shutting down on me

---

### Post by broekskw on 2008-03-01
sorry here is my system log . ok firefox closed again

---

### Post by jan quark on 2008-03-01
are these the messages before a hang up?
it would be nice to have the whole sentence not only a truncated version :)

if your firefox freezes you can run it via the terminal by typing 
```
firefox 
```
into the terminal

the next time it crashes you should see some error messages in the terminal
which should help us to identify the problem


edit: have to quit for two hours or so. but will look at this thread when I come back

---

### Post by broekskw on 2008-03-01
great just opened firefox in a terminal , now just wait and see:popcorn:

---

### Post by broekskw on 2008-03-02
did some more reading about this and it looks like the extra memory that i installed was causing the problem, took out the memory and all is good:guitar:, no more black screen:lolflag:

---

