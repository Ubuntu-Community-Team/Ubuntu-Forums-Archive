---
title: "Problem with Sound!"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by durundal on 2006-12-14
I don't know if this is happening to anyone else but in Edgy the volume control doesn't work! When I mute the computer, it doesn't mute firefox or other programs, its not only mute but any change in the volume only seems to effect my mp3 player and does nothing to the sound in any other program!  Why can't it just mute everything? How can i get it to work? ](*,)

---

### Post by xyz on 2006-12-14
> **durundal said:**
> I don't know if this is happening to anyone else but in Edgy the volume control doesn't work! When I mute the computer, it doesn't mute firefox or other programs, its not only mute but any change in the volume only seems to effect my mp3 player and does nothing to the sound in any other program!  Why can't it just mute everything? How can i get it to work? ](*,)
In a terminal, run
[code]alsamixer[/b]
and see what's in there! Mute, umute..
Also:
Applications > Sounds Videos > Volume control
See if it works!

---

### Post by durundal on 2006-12-14
ahh, i ran alsamixer and it appears that when i turn the volume up and down only "PCM" is changing but "Front" is up all the way and does not change.  

How can i change the value of this and is it possible to be able to change the volume of them both simultaneously?

---

### Post by xyz on 2006-12-14
Hi,
Not sure what you mean by "Front"?
When I run "alsamixer" I see no Front!

---

### Post by durundal on 2006-12-14
Well it could just be me then... i dont know what it means either but it is there and apparently on my computer it controls the volume for nearly everything...

when I run alsamixer it gives me a graphical interface with the options of: PCM, Front, Front Mic, Surround, Center, LFE, Line, CD, Mic, PC Speaker, Caller ID, Channel Mode, and three mic Input Sources

so i guess I need to find a way to get the volume control for PCM and this "Front" to work together, do you think it is possible to do this?

---

### Post by xyz on 2006-12-14
Just a thought...when you go...Applications > Sounds & Videos > Volume Control > Edit > Preferences
Do you also see "Front"in there and is it checked if so?

---

### Post by durundal on 2006-12-14
Yeah its in there, but it wasn't checked when I first looked, i had to check it so I could control it.

---

### Post by xyz on 2006-12-14
Darn...sure would help if I had that darn Front!
Found this...check out what **crichell**
Hopefully....let me know even if I'll have to log out soon!
Good luck!
[http://ubuntuforums.org/showthread.php?t=242996](http://ubuntuforums.org/showthread.php?t=242996)

---

### Post by durundal on 2006-12-14
oh yes! sorry! i forgot to mention i have a laptop with built in speakers maybe thats why i have "front"? 

Thank you for the link though looks like the binding thing might work but i have to go to work perhaps i will bump this thread later with results.

---

### Post by Jussi01 on 2006-12-14
You can right click on the volume control Icon in the corner and click preferences - then you can choose which thing your volume setting controls. I had a lot of trouble with this... if you need help with binding your key pm me and we can talk on Irc or something.

---

### Post by xyz on 2006-12-14
> **durundal said:**
> oh yes! sorry! i forgot to mention i have a laptop with built in speakers maybe thats why i have "front"? 

Thank you for the link though looks like the binding thing might work but i have to go to work perhaps i will bump this thread later with results.
I've got a lapptop. Got to go too. See you around!

---

