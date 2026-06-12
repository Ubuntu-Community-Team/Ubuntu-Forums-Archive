---
title: "Beryl and music/media players wont work together"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by SMS on 2007-07-07
hey guys,
been using beryl for a few weeks on feisty and it rules, but if i have beryl running and i try to load up a media player, xine for example, it opens but then immediately crashes, if i open it in terminal i get this

sms@sms-laptop:~$ xine
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2108
  Current serial number in output stream:  2109
sms@sms-laptop:~$ 

but if i use gnome i can use xine perfectly,
any ideas why they wont be friends lol
thanks guys

---

### Post by razeshkale on 2007-07-07
Yah i have same problem
wheni start using Beryl and try to start any movie it gets Black screen!!
but i can listen sound n all
so i thinks it something with Display Compatibility issues
I have Dell 1420 and 700m
both has same problem

---

### Post by overdrank on 2007-07-07
> **SMS said:**
> hey guys,
been using beryl for a few weeks on feisty and it rules, but if i have beryl running and i try to load up a media player, xine for example, it opens but then immediately crashes, if i open it in terminal i get this

sms@sms-laptop:~$ xine
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2108
  Current serial number in output stream:  2109
sms@sms-laptop:~$ 

but if i use gnome i can use xine perfectly,
any ideas why they wont be friends lol
thanks guys

Hi and the insufficient resources make me think of not enough ram, just a thought.:-k

---

### Post by SMS on 2007-07-07
lol atleast u get sound mine just opens and closes

---

### Post by SMS on 2007-07-07
i have 1.86GHZ and 1Gb or RAM

---

### Post by overdrank on 2007-07-07
> **SMS said:**
> i have 1.86GHZ and 1Gb or RAM

That is good but how much ram is dedicated for the video.

---

### Post by SMS on 2007-07-07
up to 128Mb (it changes according to how much is needed)

---

### Post by Waappu on 2007-07-07
Hi

See if this helps
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl](http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl)

---

### Post by berserker on 2007-07-07
I had to downgrade xine-ui to version 0.99.4-0ubuntu6 in order for xine to run in Beryl.

---

### Post by SMS on 2007-07-07
thanks Waappu worked perfectly *listening to my music"

---

