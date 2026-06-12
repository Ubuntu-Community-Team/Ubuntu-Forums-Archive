---
title: "Pidgin won't open"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by TGCIL on 2007-12-19
I've tried searching for solutions and I haven't found anything that has helped. I'm a recent convert to Linux and still trying to figure things out. This may be more of a problem with pidgin then linux but, I've started using pidgin since I've been using linux and when I went to boot start it it'll show pidgin at the bottom for about half a minute and it says starting pidgin internet but then disappears without bringing up anywindows, any ideas? I would try running it in the terminal but I don't know the command sequence

---

### Post by Lord_Dicranius on 2007-12-20
Just type:

```
pidgin
```

into a terminal.  If there's any issues, it should output some errors in the terminal when Pidgin closes after that half minute.  If there's errors, post 'em here and we can take a look :)

---

### Post by nowshining on 2007-12-20
in terminal u can just try typing pidgin

are u using ubuntu or kubuntu?

did u check in the notification area as it could of auto minimized from last time - it may do that by default to start up the exact way u had last exited it. I: had the same prob. then looked in the notification area and it was there.. :)

---

### Post by TGCIL on 2007-12-20
when i typed pidgin in terminal there was no output it returned with username system name waiting for command.

I've got Ubuntu, I tried uninstalling and reinstalling it and there was no change how do I check on the auto minimize?

---

### Post by nowshining on 2007-12-20
did u make sure there was not or was a icon in ur notification area -- look real closely...or re-try and wait 5m to see if it shows up.

if not then come back and let us know.

---

### Post by nowshining on 2007-12-20
u know scratch that

i just remembered

try this

open up system monitor 

system -- administration -- system monitor

go to the processes tab and find all the pidgins if any and press the ctrl key and hold it down press the last pidgin in the row and let go of the ctrl key, at the bottom end process and when asked do so, u can re-starting now, if not re-do what i just typed out and then go into places -- home, press ctrl + h, find .purple and delete it- try starting up pidgin now.

---

### Post by TGCIL on 2007-12-21
Tried doing processes no pidgins showed up when I deleted purple it seems to be working now, much thanks

---

### Post by nowshining on 2007-12-21
great, then pidgin was not started then, yeah i thought .purple the pidgin preference folder might of been the cause 'cause i think i had to delete that after some thought i did remember.

and ur quite welcome TGCIL

---

