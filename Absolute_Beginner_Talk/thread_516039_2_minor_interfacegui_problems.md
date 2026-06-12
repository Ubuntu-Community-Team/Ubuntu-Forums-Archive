---
title: "2 minor interface/gui problems"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by pitseleh on 2007-08-02
I've got too small issues that I'm not sure how to go about taking care of. The first one involves my red Log Off button. When I installed Ubuntu, it defaulted to the far top right corner (and I really liked it there), but it has moved over to the left side of the clock and active program bank like this:
[Screenshot]("http://smg.photobucket.com/albums/v14/braincandy/?action=view&current=Screenshot-1.png")
The first time it returned on restart, but this last time, it seems to think it's new home is where it moved itself too. I'm not too concerned about it randomly moving over, but how do I get it back to it's original location? I unlocked both panels and tried dragging it over but with no luck. It seems like it's super simple, I just can't get it to migrate.

The second problem... which is also no big deal, is when I turn on the wobbly window desktop effect, most of the programs title bars (with the minimize, maximize, close buttons) disappear and are left with a white border around the program. This happens with Firefox and most larger programs, but not EmEsEne and GAIM. I know the desktop thing is experimental, and I'm most likely not running the right video driver, but I thought I'd throw that out there in case it's a common problem. I'd screen cap it, but the screenshot program does not work when that desktop effect is enabled.

---

### Post by kens8 on 2007-08-02
I'm not sure about the Log Off button thing.  Are you using a widescreen monitor?  I seem to remember something like that happening to me when I switched to my widescreen, until I got the right resolution set.

But, about the wobbly window effect - the same thing happened to me.  I ended up just installing Beryl, since it runs MUCH faster and has so many other customizable features.  [Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29")'s a good howto if you're using NVIDIA.  If you're using ATI just go up a little on the page.

---

### Post by atomkarinca on 2007-08-02
you can change its location back like this:

right-click on the icon you want move and deselect "lock to panel" then move it wherever you want by middle-click or right-click and select move, finally right-click and select "lock to panel".

edit: and for the second one you can try this (but i'm not sure if it definitely works):

system > administration > restricted derivers manager and enable your nvidia driver.

---

### Post by p_quarles on 2007-08-02
Dragging doesn't work with all panel icons, I've found. The same thing happened with my power icon, and I was able to fix it by right-clicking, unlocking it, then right-clicking and selecting "move." Then it moves with the mouse until you left-click.

---

### Post by pitseleh on 2007-08-02
Thanks! I was able to get the power button back in it's spot by unlocking both panel sections (the one with the clock must've locked itself back up), then I used the move function instead of dragging it. I found that I could not get the button on the right side of the clock, so I deleted the clock and moved the power button all the way over then re-added the clock. So that's all set.

I'm running Ubuntu on my [IBM Thinkpad X31]("http://www.thinkwiki.org/wiki/Category:X31"), so no widescreen or anything. I thought that on the off chance that the wobbly window worked, I'd use it (it's pretty spiffy), but I doubt my  ATI Mobility Radeon 7000 can run any aspect of Beryl. Or can it? There is some info on it here:
[ATI Mobility Radeon 7000]("http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000")

I have not done anything to try and upgrade or tweak my video drivers. I've always been afraid that I'll just muck it up.

---

### Post by kens8 on 2007-08-03
Yeah, the Beryl website does suggest a 7500 or better, but it's worth a try.  I experienced way too much slowdown with the built-in effects.  It wan't unusible, but it was way too annoying.

---

