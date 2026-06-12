---
title: "want to run game from home folder or usr/games - with launcher"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by mike_m on 2007-09-10
Ok, I downloaded a game for linux called barrel_patrol_3d.0.90, I untared it to my desktop & it runs fine. * docs say no need to install or compile.

So I tried to move the folder to my home & make a launcher for it so I wont have this folder on my desktop, launcher wont run it, so I guess it's the folder permissions, so I "chmod 777 -R /home/mike/barrel_patrol_3d.0.90" still wont run from launcher. I was going to move it to usr/games/ (where all the other games are) but I think I'll still have the same problem. I did't want to chmod my home folder because doesn't that help protect me somehow?

What should I do?   Thanks in advance, Mike

---

### Post by kellemes on 2007-09-10
You need to make the executable executable.. chmod +x nameofexecutable.

---

### Post by mike_m on 2007-09-10
well I did your idea "make the executable executable.. chmod +x nameofexecutable"
& tried to run it in my home folder & in usr/games & both times I got "Segmentation fault (core dump)" Then I tried all kinds of permissions combinations, even looked at the other games in usr/games to get their  permissions to copy, still no luck? I guess I'll just run it from the desktop, but I'd like to learn why I can't do this.
Maybe I forgot to say it has a total of 3 files, the game + 2 data files.

check it out here > [http://www.fathomgames.com/downloads.html](http://www.fathomgames.com/downloads.html) (also screen shots)
It is a cool game with good graphics :) 

Thanks again for the input, Mike

---

