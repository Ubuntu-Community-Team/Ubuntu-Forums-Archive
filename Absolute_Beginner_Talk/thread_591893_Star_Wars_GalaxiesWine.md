---
title: "Star Wars Galaxies\Wine"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by TuxIsCute on 2007-10-25
I would like to play Star Wars Galaxies (SWG).  I used wine and it installed perfectly but when it goes to go in-game it crashes.  I then tried the newest cedgea and it doesn't support SWG since the NEG which was back in 2006.  I would like anyone out there that may have gotten this to work to tell me (in dumbed down english) exactly how to get it to work!

Please help a fellow SWGer out!

TUXISCUTE

---

### Post by Maestro23 on 2007-10-25
Have you check the Wine DB for any help with SWG?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3089](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3089)

---

### Post by TuxIsCute on 2007-10-25
Yes, I have.  There are many people that say they've gotten it to work but none say HOW!

I have read time and time again that some things have to be added  to the registry to get it to run, but no one seems willing to tell what those changes are!

---

### Post by fain on 2007-10-25
i had it working a couple months ago b4 i let my account expire. I just copied it over from my windows partition and started it with a launcher with this in it.

```
env WINEPREFIX="/home/youruserhere/.wine" wine "C:\Program Files\Sony\Station\Launchpad\LaunchPad.exe" /game:starwars
```

the only things i have done to the registry is what needs to be done with wow to get it working. From here.

[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

not sure if that has any thing to do with it or not. It doesn't run perfectly but its good enough to play.

hope this helps.

---

### Post by TuxIsCute on 2007-10-29
This doesn't work.  It will get to where it's loading terrain but then it crashes to the desktop.  The program doesn't read it as a crash eitther, so I think it's wines fault.  i don't know what's causing it.  I'm going to run it fromterminal and see what it says when it crashes out.  I'll post that here later after I try it.

---

### Post by TuxIsCute on 2007-10-30
fixme:d3d:state_psize >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1261

This is what I get as an output in terminal can anyone fix it?

---

