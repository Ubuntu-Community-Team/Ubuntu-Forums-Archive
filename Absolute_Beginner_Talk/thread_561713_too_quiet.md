---
title: "too quiet"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by FKi on 2007-09-27
i love music.  my sound is working fine as always. but i was wondering, these headphones are kind of quiet, is there any way i can modifie what the max volume on the system is? because everything is turned up but its just not quenching my thirst.

---

### Post by Pumalite on 2007-09-27
Check your board for a sound key. In some systems/keyboards, the volume is additionally controlled with the board.

---

### Post by Dr Small on 2007-09-27
Before you preform the following command, be sure to plug your keyboard into the correct input in your brain.

Then type this command:
```
amixer set Master 50%
```

That should help adjust your thirst level :D

---

### Post by LowSky on 2007-09-27
what is amixer normally set to?

---

### Post by jordanmthomas on 2007-09-27
depends on what you have set it to.
To adjust all your volumes easily, check out the 
```
alsamixer
``` command on your friendly terminal emulator.
Look into raising Master, Headphone, and PCM values.  (I don't like to put PCM over about 70% because it makes the sound quality go waaay down.)

---

### Post by Dr Small on 2007-09-27
I had to go as far as logging onto IRC to find out that command, because I forgot the spelling, and then you go and post it... I should have just waited :|
Lol.

Dr Small

---

### Post by enopepsoo on 2007-10-05
Thanks for the tip.  alsamixer fixed it right up.

---

### Post by FKi on 2007-10-10
ok so iv pumped everything up in alsamixer, everything is 100%, but yet my headphones still arent loud enough :(, am i just going def?

Is there anything else i can do?

---

### Post by Dr Small on 2007-10-10
You are so used to loud music that you are going deaf :p

---

