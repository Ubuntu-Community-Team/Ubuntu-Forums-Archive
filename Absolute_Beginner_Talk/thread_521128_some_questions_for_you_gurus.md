---
title: "some questions for you gurus"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by suZM on 2007-08-09
problem 1) I got a saitek eclipse keyboard and i cant get the volume controls on it to work at all. the ubuntu volume control panel adjusts visually when i try it but the actual volume never changes.  im using xmms for music right now and i just cant adjust the volume in that program at all even if i move the volume bar around nothing changes its always at the same volume. so what kind of solutions do you guys got for that?

problem 2) i want to get steam up and running (for cs 1.6) and i got it going through wine but the fonts arent there and yes i know you need the tahoma.tff font in the fonts file in the wine file but im still not getting any fonts ive even dumped a crap load of other fonts in there to see if itll pick one of em up and im still not gettin anything? 

problem3) i hate that loud noise that ubuntu makes when it loads, how can i turn that sound off?


i hope you guys understand my questions, and can help with solutions because besides these three little things ive gottin the o.s. running flawlessly now it i just gotta patch up the little annoyances.
bear with me for _i am a linux noob_, thanks before hand.

---

### Post by Tiekyl on 2007-08-09
1...have you tried changing the settings under System..Preferences..Sound..then looking at hte default mixer tracks? I had to set mine to "Front" for it to work...

3...are you talking about the bump noise? I think you can turn it off in the sound preferences under sounds..then log out / in.

---

### Post by ZipoTe on 2007-08-09
> **suZM said:**
> 
problem3) i hate that loud noise that ubuntu makes when it loads, how can i turn that sound off?



lol!! this was the first i did when installing ubuntu :D

---

### Post by amrclutch1 on 2007-08-09
suZM I have to break it to you. I also am a gamer, I play css everyday. Believe me, I got it running the best I can on a 7950GT and it runs terribly. 50-60FPS max and the textures look horrible compared to Micro$hit's Windbl0w$. The only thing I hate about linux is the gaming, if linux would be the mainstream OS the world would have a revolution, everything would run smoothly, games would run good on linux. After my experience, just create a 10GB partition for windows and dual boot, set GRUB (The boot loader) to default select to Ubuntu, and you can select Windows or Ubuntu on boot. Believe me, you don't want to play with wine on counterstrike, your skills will be horrible.

---

### Post by zero-9376 on 2007-08-09
1. sounds like the volume control is changing the wrong mixer, i had this issue once before, have a search on here for ac97 quirk, its some module option for certain hardware.
  for the keyboard volume control open up a terminal and use the command xev, put your mouse in the black square and press the keyboard volume control, you can then use gconf-editor to set this up or if you havent tried it use keyboard shortcuts in the preferances menu. 
 might also want to go to preferences sound and make sure its ouputs are set to use ESD, you may also have to do something similar in xmms (or install audacious, which is a newer winamp clone)
2. no idea, i didnt even know it ran under wine, you could look at crossover but its commercial
3. system - preferances - sound - sounds tab

---

### Post by AlexenderReez on 2007-08-09
> **suZM said:**
> problem 1) I got a saitek eclipse keyboard and i cant get the volume controls on it to work at all. the ubuntu volume control panel adjusts visually when i try it but the actual volume never changes.  im using xmms for music right now and i just cant adjust the volume in that program at all even if i move the volume bar around nothing changes its always at the same volume. so what kind of solutions do you guys got for that?

problem 2) i want to get steam up and running (for cs 1.6) and i got it going through wine but the fonts arent there and yes i know you need the tahoma.tff font in the fonts file in the wine file but im still not getting any fonts ive even dumped a crap load of other fonts in there to see if itll pick one of em up and im still not gettin anything? 

problem3) i hate that loud noise that ubuntu makes when it loads, how can i turn that sound off?


i hope you guys understand my questions, and can help with solutions because besides these three little things ive gottin the o.s. running flawlessly now it i just gotta patch up the little annoyances.
bear with me for _i am a linux noob_, thanks before hand.

> **ZipoTe said:**
> lol!! this was the first i did when installing ubuntu :D


starting from Gutsy..there will be no sound and splash screen at startup because want to make it fast:)...

about sound....give a look at-->
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by suZM on 2007-08-09
thanks a lot guys now i just gotta get this font working, and as for  amrclutch1  i know linux is horrible for gaming thats the only thing thats completely stopping me from switching over (for i am dual booting xp & ubuntu).  i dont particularly wanna run any gfx heavy games i just want cs 1.6 (being the one that came out in 1998 not source) to work cause im playing that a lot right now. but again thanks for all the tips guys.

---

### Post by splintercellguy on 2007-08-09
> **amrclutch1 said:**
> suZM I have to break it to you. I also am a gamer, I play css everyday. Believe me, I got it running the best I can on a 7950GT and it runs terribly. 50-60FPS max and the textures look horrible compared to Micro$hit's Windbl0w$. The only thing I hate about linux is the gaming, if linux would be the mainstream OS the world would have a revolution, everything would run smoothly, games would run good on linux. After my experience, just create a 10GB partition for windows and dual boot, set GRUB (The boot loader) to default select to Ubuntu, and you can select Windows or Ubuntu on boot. Believe me, you don't want to play with wine on counterstrike, your skills will be horrible.

Not so sure about Wine sucking so bad, your mileage may vary. That said, have you checked out the AppDb? And 50-60 FPS is great, faster than what our eyes can do.

---

### Post by suZM on 2007-08-09
> **splintercellguy said:**
> Not so sure about Wine sucking so bad, your mileage may vary. That said, have you checked out the AppDb? And 50-60 FPS is great, faster than what our eyes can do.

see the thing is is that i got an 8800 4600+ 2gb of 800 i think it will be able to "emulate" a game thats ten years old pretty decently id imagine. ive talk to a few ppl in irc saying how they got it runnin under other linux distro such as gentoo and fedora but never asked what they were emulating it with

---

