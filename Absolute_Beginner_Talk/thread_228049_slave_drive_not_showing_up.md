---
title: "slave drive not showing up"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-02
i tryed the has this already been asked thing but the bandwidth is reached it said to many ppl on or something like that but anywas i just switched to ubuntu today from windows and i have no experince with linux at all so sorry if i make no sense. but anywas i have 2 issues i cant seem to solve 

1. my secoundary or slave hard drive does not show up or well i cant seem to find it. it isnt a partition it is an secound drive so i dont think any of the other posts about how to partition are any help to me :( but how can i bring this drive up without harming all the files i have saved on there such as my music and movies?

2. i happen to be a gamer and one of my absolute favorite games is wolfenstein enemy territory and well i found a guide on unbuntu for installing the game and i followed it as best as i could and its installed and everthing but... the game does not start up :( i click on the program which is located in my applications/other/ thing and my screen goes black like its gonna start up and it dont instead it makes everthing i had open like 4 times larger and i have to scroll to do cretain thing and i cant seem to exit this without restarting my computer.

these are my two problems also note that the ET game is my first attempt at installing a program/game with linux thank you for your time and i didnt mean to make it so long XP

---

### Post by aysiu on 2006-08-02
It's the same procedure to mount a drive as it is to mount a partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by kthakore on 2006-08-02
if that doesn't work than try 

typing 

```
sudo mount -a
```

usually works or 

```
sudo killall nautilus
```

type this in the terminal, the terminal is located in programs >applications

---

### Post by nixclusive on 2006-08-02
> **kingvicious said:**
> 
...stead it makes everthing i had open like 4 times larger and i have to scroll to do cretain thing and i cant seem to exit this without restarting my computer.


I don't know how to fix that game, but yeah, you don't have to restart the computer to get out of that 4-times thing. Just restart the X-Server by pressing Ctrl-Alt-Backspace and you should have a relogin screen.

---

