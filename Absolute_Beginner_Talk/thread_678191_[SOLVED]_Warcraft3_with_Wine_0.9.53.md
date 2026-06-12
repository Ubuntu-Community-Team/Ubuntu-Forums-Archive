---
title: "[SOLVED] Warcraft3 with Wine 0.9.53"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by ErrorMsg on 2008-01-25
Hi everyone,
I've got a little problem with Warcraft3 running under Wine. When I first installed Wine through Synaptics (I believe that was how I installed it) the campaign wouldn't work. I read somewhere that a newer version of Wine works better, so I added a newer version of Wine to the repository, installed that and everything works great now. (I read somewhere that it wasn't recommended, but... oh well, it was just a recommendation ;) ) Performance is a blast in opengl-mode, campaigns work, and I didn't even install that game to the fake C_drive but run it off of my fat32-partition I also use in Windows. I believe that is not recommended as well. I just like crossing lines I guess.
Horizontal scrolling doesn't work however. When I move the mouse to the top or bottom of the screen it works fine, but when I move it to the side, the cursor switches from the Warcraft3 cursor (which is a hand, I believe) to the normal arrow I use on my desktop and it doesn't scroll. It's like the mouse moves a pixel over the edge of the program's window or something (even though it's fullscreen), I'm just wondering if you guys know some trick to get the horizontal scrolling to work properly. Maybe there's a way to restrict the mouse to stay inside the window or prohibit it from changing contexts or whatever, don't really have an idea, I guess.
It's the most recent version of Warcraft, got the latest patch through battle.net in Windows, and Wine is, like I said, version 0.9.53. I found a few people having the same problem through google, but no solution to it.
I'm not totally new to Linux either, so you don't really have to handfeed me, just give me a direction, if possible. :)
Thanks!

---

### Post by Lord Illidan on 2008-01-25
Try disabling window manager managed windows in winecfg
EDIT : Oh and btw, welcome to the forums.

---

### Post by skymera on 2008-01-25
hi 

i find new versions of Wine arent always the best.

0.9.46 was good, however 0.9.47 wasnt.

anyway in winecfg (enter in the terminal) uncheck "Window managee can control apps" (or something similar)

might fix it

if not run in a vitrual desktop, should be an option in winecfg

---

### Post by ErrorMsg on 2008-01-25
> **Lord Illidan said:**
> Try disabling window manager managed windows in winecfg
EDIT : Oh and btw, welcome to the forums.
doh, should have seen that...
worked perfectly, thanks for the hint and quick response.
and thanks for the welcome. :)

---

### Post by skymera on 2008-01-25
well glad its working :)

and Lord Illidan beat me by a few seconds XD

---

### Post by Lord Illidan on 2008-01-25
I just checked it over here : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

I love WC 3, as you can very well see :D

---

### Post by ErrorMsg on 2008-01-25
> **skymera said:**
> hi 

i find new versions of Wine arent always the best.

0.9.46 was good, however 0.9.47 wasnt.
Yeah, I read that for some apps downgrading wine might be helpful.
Counterstrike 1.6 (Steam) worked with 0.9.46 just as good as with 0.9.53 however, Warcraft3 works better with the newer version. Those are the two programs I have tested as of now, the Pokerstars-Software worked with the old version (except for resizing the windows, but that's a known problem and there's a solution to it on the web somewhere, I think), haven't tried it with 0.9.53 however. It's got Platinum-status on winehq.org though, so it shouldn't be a problem.
I want to try more games, but I've got the important stuff on Ubuntu now. Doom3 and Quake run nativley, so I don't have to worry about them (thank god :)).

---

### Post by Lord Illidan on 2008-01-25
I also recommend UT 2004..

---

### Post by ErrorMsg on 2008-01-25
> **Lord Illidan said:**
> I also recommend UT 2004..
Yeah, liked that one too, never played it as much as Q3A though.
Stalker would be a nice thing to have in ubuntu, but it barely runs with windows on my machine... will try that in the next few weeks though, just so I know for sure. :)

---

### Post by running_wild on 2008-01-27
With the version 0.9.54 , can we host in battlenet? i tried but whit no results :(

---

