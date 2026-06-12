---
title: "Installing Flight Gear"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-11-26
Hei, Ive tried to install flight gear flight sim on ubuntu. its seems to install fine(installed through synaptics), bu I have no idea how to start it - it doesnt appear in any of the menu's or anything. What am I doing wrong?

---

### Post by djsroknrol on 2006-11-26
Type this in a terminal:

```
fgfs
```

You can add Flight Gear to your menu with alacarte in Applications>Accessories

---

### Post by matthew on 2006-11-26
You haven't done anything wrong. I just installed it to check this out for you and the program doesn't automatically install anything in the menus. What you can do (and this wasn't obvious to me either) is open a terminal (Applications->Accessories->Terminal) and type this at the command line to start the program:```
fgfs
```I'm guessing it stands for Flight Gear Flight Simulator.

I haven't tried the program out to see how it works or anything, but it started up that way for me.

---

### Post by matthew on 2006-11-26
Quick followup:

I can't get the game to work on Edgy...I keep getting a seg fault. Is anyone else experiencing this? It seems to be looking for a file in a hidden directory in my /home that was never created...in fact it never creates the .fgfs directory at all. Anyway, here's the error message:
```
matt@telecaster:~$ fgfs
Error reading properties: 
Failed to open file
 at /home/matt/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
Segmentation fault (core dumped)

```

---

### Post by Jussi01 on 2006-11-26
Nah mine looks fine - thanks a lot!! your a star:KS

---

### Post by djsroknrol on 2006-11-26
> **matthew said:**
> Quick followup:

I can't get the game to work on Edgy...I keep getting a seg fault. Is anyone else experiencing this? It seems to be looking for a file in a hidden directory in my /home that was never created...in fact it never creates the .fgfs directory at all. Anyway, here's the error message:
```
matt@telecaster:~$ fgfs
Error reading properties: 
Failed to open file
 at /home/matt/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
Segmentation fault (core dumped)

```


Matthew, when I installed Flight Gear thru Synaptic, it installed to:

/usr/games

Strange it would install to your /home dir.....

---

### Post by matthew on 2006-11-26
> **djsroknrol said:**
> Matthew, when I installed Flight Gear thru Synaptic, it installed to:

/usr/games

Strange it would install to your /home dir.....It installed to /usr/games, it just seems to be looking for a config file (autosave.xml) in /home/.fgfs and isn't finding it because that directory doesn't exist. Does it exist for you?

---

### Post by djsroknrol on 2006-11-26
> **matthew said:**
> It installed to /usr/games, it just seems to be looking for a config file (autosave.xml) in /home/.fgfs and isn't finding it because that directory doesn't exist. Does it exist for you?

I'll be darnned....I honestly haven't played in quite some time, and the last time I did it worked fine...but now I'm getting the same thing...very odd...hope someone has a cure for this...

Are you running Beryl?...That's the last major thing that I installed, besides IE4Linux....I'm wondering if one of those programs pooched my install of fgfs....

---

### Post by matthew on 2006-11-26
> **djsroknrol said:**
> I'll be darnned....I honestly haven't played in quite some time, and the last time I did it worked fine...but now I'm getting the same thing...very odd...hope someone has a cure for this...

Are you running Beryl?...That's the last major thing that I installed, besides IE4Linux....I'm wondering if one of those programs pooched my install of fgfs....Weird...I'm not running beryl (or compiz). I can't see any reason why it isn't working unless there's either a dependency that has changed since the .deb was built or perhaps there was a problem with the package itself. Hmm...

---

### Post by djsroknrol on 2006-11-26
> **matthew said:**
> Weird...I'm not running beryl (or compiz). I can't see any reason why it isn't working unless there's either a dependency that has changed since the .deb was built or perhaps there was a problem with the package itself. Hmm...

But that wouldn't explain why my install stopped working...it's been about 3 weeks since I messed with it, and it was working then....very odd....

---

### Post by matthew on 2006-11-26
> **djsroknrol said:**
> But that wouldn't explain why my install stopped working...it's been about 3 weeks since I messed with it, and it was working then....very odd....Hmm... <cue Twilight Zone music>

---

### Post by djsroknrol on 2006-11-26
Well, I solved my problem with it...seems like when I added it to my menu, I pointed to the folder that had all my game links in...DUH!!...my install works fine as you can see....

---

### Post by matthew on 2006-11-27
> **djsroknrol said:**
> Well, I solved my problem with it...seems like when I added it to my menu, I pointed to the folder that had all my game links in...DUH!!...my install works fine as you can see....Well, that's good anyway. Sigh. Another thing to add to my low-priority "when I have some free time" list. :)

---

### Post by Sico on 2007-03-04
I had the same problem (was unsure how to run).  Thanks! This thread helped me.

---

### Post by rne1223 on 2007-08-16
> **djsroknrol said:**
> Well, I solved my problem with it...seems like when I added it to my menu, I pointed to the folder that had all my game links in...DUH!!...my install works fine as you can see....


Huh?..What do you mean by "pointed to the folder that had all game links in"? How do you do it?

---

