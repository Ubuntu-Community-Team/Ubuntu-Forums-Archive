---
title: "WoW, Wine, SLI Problem"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by tito13kfm on 2007-06-08
Hi all, First post here.  It's a World of Warcraft/Wine problem.

I'll get right to the problem I'm having.

I'm running Ubuntu Feisty Fawn 7.04
Nvidia Drivers: 100.14.03
SLI is enabled through my xorg.conf file

SLI mode seems to be working while logging in and in the Load screen but it seems to stop as soon as I enter the game world.  I first noticed this by having 0 fps difference from SLI being on and off.  I wanted to verify it so I turned on the little OpenGL SLI meter in the nvidia options.

Some screenshots to show I'm not crazy.

During Load Screen
[http://i16.tinypic.com/4otri8j.jpg](http://i16.tinypic.com/4otri8j.jpg)

In Game
[http://i9.tinypic.com/67d7a5e.jpg](http://i9.tinypic.com/67d7a5e.jpg)

Just looking for some guidance and some suggestions on what I can try next.  Let me know if you need any more information.

Thanks
Tito

---

### Post by machoo02 on 2007-06-09
Have you looked at the WoW page at the [WINE application database]("http://appdb.winehq.org") for any suggestions?

---

### Post by tito13kfm on 2007-06-10
Yes, the AppDB was the first place I checked.

After messing around with my SLI settings it seems that WoW or Wine or the combination of both and my video cards doesn't want to use AFR (Alternate Frame Rendering) during game play.  I semi solved this problem by switching to SFR (Split Frame Rendering) mode.  The SLI Heads-up display shows activity on both cards while playing in SFR mode, but I must admit the framerate gain is negligible in Wine+WoW.

For now I will use AA SLI mode as I'm able to get the same frame rate with 4x AA on as with it off as long as I use the second card for nothing but Anti-aliasing.

I guess I will have to wait for a newer version of Wine before I try AFR again.

---

### Post by machoo02 on 2007-06-10
You could also check out [Crossover]("http://www.codeweavers.com"), the commercial implementation of WINE.  I hear that they have had good success in getting WoW working fairly well.  You can get a 30 day free trial, and if you decide to purchase it, you can feel good as they are the main financial contributers to the WINE project (as well as employing several WINE developers)

---

### Post by FleetAdmiral74 on 2007-06-10
> **machoo02 said:**
> You could also check out [Crossover]("http://www.codeweavers.com"), the commercial implementation of WINE.  I hear that they have had good success in getting WoW working fairly well.  You can get a 30 day free trial, and if you decide to purchase it, you can feel good as they are the main financial contributers to the WINE project (as well as employing several WINE developers)

Is cross over open source? Or is it closed, but still supports WINE for some reason. And how does this compare/differ with something like Cedega, which also is not free, but has very good success with games.

---

### Post by machoo02 on 2007-06-10
Check out [this page]("http://www.codeweavers.com/about/philosophy/") that basically states what Codeweavers is all about.  Basically, they make some proprietary changes to wine, put it together with a graphical installer, and guarantee support (i.e., that they will run) for a small range of software (mainly MS Office, some Adobe products, and now growing support for games).  Eventually, all the improvements that they make to the Wine codebase go back to the Wine project eventually so everyone benefits.  This is different from Cedega in that they *actually* contribute to the Wine project, instead of just taking the code and not sharing their improvements (i.e., Direct3D stuff).  I'm sure there are discussions on the merits of both over in the Gaming section of the forum.

---

