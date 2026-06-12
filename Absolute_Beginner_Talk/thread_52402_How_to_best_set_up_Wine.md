---
title: "How to best set up Wine?"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-27
Is installing Wine with synaptic sufficient, or should one use Winetools to properly set up and install Wine?? Where does all the simulated windows junk go when it's installed using Winetools? Also how do you install windows software that normally installs with an installer requiring a serial number? Do you run the installer with Wine? Lot's of questions...

---

### Post by sonny on 2005-07-27
It is enough with the synaptics install, and then configure little, by typing wine and just accepting the defaults, that should work fine.

The Windows drive is under: /home/username/.wine/fake_windows
that is where all windows apps are installed, after fake_windows, you'll find a c: drive with a Windows folder, a Documents and Settings folder, and so on.

You just have to execute the installer.exe file, and it will install as if you were in windows, if you need a serial you will be prompted by the installer.

For more info about wine you can go to:
[http://www.winehq.org/](http://www.winehq.org/)
[http://frankscorner.org/](http://frankscorner.org/)

---

### Post by grofaz on 2005-07-27
Thank you, I'll give it a shot. What is the difference between Cedega and plain Wine?

---

### Post by sonny on 2005-07-27
Cedega is more likely to run games, and manage the DirectX stuff, meanwhile plain Wine is just for some apps (although the list is big) and some games, in frank's corner there's a bunch of how-to's in running games and apps with wine.

---

### Post by poofyhairguy on 2005-07-27
[QUOTE=grofaz]Thank you, I'll give it a shot. What is the difference between Cedega and plain Wine?[/QUOTE]

Cedega is configured to work best with games.

---

### Post by grofaz on 2005-07-27
Will cedega run ANY game or are you limited to pre-packaged games? I don't play FPS's et al. I play mostly isometric type hex based games a la Panzer Campaigns, Flashpoint Germany, War in the Pacific. etc. Where is Frank's Corner? I need to take a look. As always...THANKS!

---

### Post by grofaz on 2005-07-27
Oops, I see the links. Thanks again.

grofaz OUT

---

### Post by grofaz on 2005-07-27
OK, I perused Frank's Corner and installed dcom98 as advised, ran the setup.exe and installed a game. Where did it go?? I can't find it and neither can wine. I tried:

wine gamename.exe

and I tried:

wine C:\\folder\folder\gamename.exe

But come up empty. What am I doing wrong?

EDIT:

Went off half cocked again! :)
Looked at the first reply above again and there she be. :))
I'll check it out...

---

### Post by grofaz on 2005-07-28
How the heck do I point wine to the game directory ? No matter what I do it says there's no such directory!

---

### Post by sonny on 2005-07-28
[QUOTE=grofaz]How the heck do I point wine to the game directory ? No matter what I do it says there's no such directory![/QUOTE]
You mean to make a link to the game?
You have to put: wine "/home/username/.wine/fake_windows/path/to/the/file.exe"

If that is not what you meant... please explain me a little more.

---

### Post by grofaz on 2005-07-28
I figured it out with the help of wine hq users guide. Wine is operational!

Now the trick is to get the games to cooperate with wine. :)

---

