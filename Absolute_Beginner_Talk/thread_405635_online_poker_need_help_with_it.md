---
title: "online poker need help with it"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by jrcullen007 on 2007-04-10
what would be the best way to get a online poker game under ubuntu 6.10 i need to get it running and new to all this linux could anyone help me through this any ideas and what not also is wine the best route and how do i go about using wine

---

### Post by deadgobby on 2007-04-10
Please post the link to the poker game you have in question
Gobby

---

### Post by jrcullen007 on 2007-04-10
well any will really do but trying to get [http://pokerroom.com](http://pokerroom.com)

---

### Post by deadgobby on 2007-04-10
Well live play has linux support.  I am not about to sign up for it.

---

### Post by jrcullen007 on 2007-04-10
yeah but it was too buggy trying to get it to work under wine just not sure how to use wine

---

### Post by jrcullen007 on 2007-04-10
i can install it fine but when i try to run it it won't it just say module not found  any help

---

### Post by justleen on 2007-04-10
why would you wanna use wine for it?

you can just use the Play Now link?

---

### Post by jrcullen007 on 2007-04-10
because wine runs it better from what i hear plus i couldn't get the instant play working so thought i would try this way

---

### Post by justleen on 2007-04-10
if you have installed wine, you should run wincfg once.
then, just execute the .exe file with  ```
 wine poker.exe 
```

---

### Post by jrcullen007 on 2007-04-10
ok in the wine cfg what am i looking for or where do i add the poker.exe

---

### Post by justleen on 2007-04-10
dont add anything in there.. just lauch it.
It wil create the directories it needs for "windows"  ( ~/.wine/drivec/ )

most progs should work with the default settings. Just close it afterwards.
Im not sure if its default, but you should be able to just right click an execuablte, and select run in Wine..

if its not in the contaxt menu, open a terminal, go to the dir with the executable and lauch it with ```
 wine <prog name.exe> 
```

---

### Post by Jussi01 on 2007-04-10
you can also play party poker without any installation - they have a java webapplet...

---

### Post by climbdahill on 2007-05-14
right, but we can't play party poker for money in the states, has anyone who plays money find a poker room that works with wine?  (note, i've gotten pokerstars and fulltilt to run on wine, but they're extremely buggy and once you sit at a table, you can't leave w/o quitting the prog. )

---

