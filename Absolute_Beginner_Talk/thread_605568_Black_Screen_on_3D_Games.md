---
title: "Black Screen on 3D Games"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by orangeLemon on 2007-11-07
I've been using Ubuntu for a few months now, and for some reason when I was using feisty my system wanted to crash when I tried to enable my graphics card, so I just waited until Gusty came out and reinstalled Ubuntu. I went through the restricted drivers manager and it enabled the nvidia-glx for me. While it has not crashed yet with the graphics card enabled, 3D games (neverball, neverputt, OpenArena) won't work, they'll come up with a black screen like so
[http://img411.imageshack.us/img411/3594/screenshotqy1.png](http://img411.imageshack.us/img411/3594/screenshotqy1.png)
Although 3D games not working appears to be the only thing wrong, beryll (sp?) still seems to be working, I can get the 3D desktop cube to work. Any help is appreciated.

Specs
Nvidia Geforce 4 MX Integrated
512 MB Ram
Approx 2 ghz processor (not 100% sure)
Ubuntu 7.10 Gutsy Gibbon 
Also dual boot with XP and 3D games work fine on it.
Any more information is needed tell me.

---

### Post by mivo on 2007-11-07
This is a long shot, but I read in some threads that people had trouble with some 3D games if they started them while a 3D composite manager (like Compiz-Fusion and Beryl) was running. It is probably not the solution, but still worth a try (turn it off and try again). Your card supports OpenGL 1.2, so it "should" be able to run these games. It's not a general 7.10 trouble since I can play 3D games fine on my box (Nexuiz, Neverwinter Nights, Warsow, some others).

---

### Post by smithman89 on 2007-11-07
> **mivo said:**
> This is a long shot, but I read in some threads that people had trouble with some 3D games if they started them while a 3D composite manager (like Compiz-Fusion and Beryl) was running. It is probably not the solution, but still worth a try (turn it off and try again). Your card supports OpenGL 1.2, so it "should" be able to run these games. It's not a general 7.10 trouble since I can play 3D games fine on my box (Nexuiz, Neverwinter Nights, Warsow, some others).

I have had this problem, either the screen would be blank or it would appear transparent.  My solution was to create 2 launchers on my desktop.  The first one which i aptly named metacity, runs the command ```
metacity --replace
```
And the second one i named compiz, and that runs the command ```
compiz --replace
``` (Note: just replace that with the beryl statement for your problem).
With this, before i enter any game or java program, i switch back to metacity and it works.  Afterwards, i switch back to compiz when i am done.

---

### Post by orangeLemon on 2007-11-07
> **mivo said:**
> This is a long shot, but I read in some threads that people had trouble with some 3D games if they started them while a 3D composite manager (like Compiz-Fusion and Beryl) was running. It is probably not the solution, but still worth a try (turn it off and try again). Your card supports OpenGL 1.2, so it "should" be able to run these games. It's not a general 7.10 trouble since I can play 3D games fine on my box (Nexuiz, Neverwinter Nights, Warsow, some others).
Didn't work, in fact I only turned on Beryl just to check to see if the 3D Cube was working to see if it was a 3D problem. I know it's not a 7.10 problem, because on 7.04 my computer completely crashed, so if anything its an improvement, but still I'd like to be able to play 3D games. 
Just tried something to see if 3D Acceleration was working (glxinfo | grep rendering) and it said that direct rendering was working.

---

### Post by orangeLemon on 2007-11-07
Topics kind of buried so posting to bump it up. (if this is against the rules please tell me)

---

