---
title: "Tremulous Crashes"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-06-06
I have been playing Tremulous recently, and for the past few days it seems to be randomly switching out of fullscreen on it's own, with no way to get back to fullscreen, close the game, or play the game. Tha only way to fix it is to restart X. I have no idea what's causing it... would anyone be able to help??

---

### Post by brennydoogles on 2007-06-07
bump

---

### Post by brennydoogles on 2007-07-01
*extra polite bump*??

---

### Post by HackingYodel on 2007-07-01
Hello friend,

I'm grabbing a copy of Tremulous now to see if I can't duplicate the crash.  What may be happening is that Tremulous is capturing all the mouse and keyboard events.  This could cause your Linux into a screensaver mode or to turn off the screen. 

Perhaps drop out of Tremulous occasionally or turn off screensavers/power saving mode?  I'll see what I can find.

---

### Post by brennydoogles on 2007-07-01
> **HackingYodel said:**
> Hello friend,

I'm grabbing a copy of Tremulous now to see if I can't duplicate the crash.  What may be happening is that Tremulous is capturing all the mouse and keyboard events.  This could cause your Linux into a screensaver mode or to turn off the screen. 

Perhaps drop out of Tremulous occasionally or turn off screensavers/power saving mode?  I'll see what I can find.

I might start up trem via terminal next time, and see if I can post the output when it crashes. Thanks!!

---

### Post by brennydoogles on 2007-07-02
> **brennydoogles said:**
> I might start up trem via terminal next time, and see if I can post the output when it crashes. Thanks!!

Ok, so neither 
```
tremulous > error.txt
```
or 
```
tremulous | cat > error.txt
```
will output what's going on in tremulous to a file, so i have no idea how to get it up here to get help. Any ideas??

---

### Post by HackingYodel on 2007-07-03
I haven't been able to reproduce your error.  I'm building a collection of my own with this game though. :)

try **tremulous 2>error.txt**  No space after 2> (2> is to send standard error to a file)

I just tried it on my system and think it's what you are looking for.

Good luck.

---

### Post by brennydoogles on 2007-07-03
> **HackingYodel said:**
> I haven't been able to reproduce your error.  I'm building a collection of my own with this game though. :)

try **tremulous 2>error.txt**  No space after 2> (2> is to send standard error to a file)

I just tried it on my system and think it's what you are looking for.

Good luck.

Here's what we've got.....

---

### Post by Aninhumer on 2007-07-12
I'va had the same problem, you just need to turn off the screensaver while playing.
It is kind of annoying, but Trem is a great game, so I don't care. :)

---

### Post by brennydoogles on 2007-07-12
> **Aninhumer said:**
> I'va had the same problem, you just need to turn off the screensaver while playing.
It is kind of annoying, but Trem is a great game, so I don't care. :)

I don't know that I even have a screensaver enabled. After 30 minutes or so my screen fades to black, but is that a screensaver?? I will see what I can do!!

---

