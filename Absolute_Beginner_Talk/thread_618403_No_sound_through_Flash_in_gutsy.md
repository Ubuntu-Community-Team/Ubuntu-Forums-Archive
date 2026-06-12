---
title: "No sound through Flash in gutsy"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bwgolling on 2007-11-20
I installed gutsy on my acer 3680.  Wifi worked out of the box (believe it or not) and after fiddling around and tweaking alsaconf the speakers are working just fine.  I added the non-free codecs and such and just about every format I can think of works fine....except
Flash.  I installed (and re-installed) the non-free package from the official repos but no go.  I also downloaded one from Adobe and it doesn't work either.  
I tried to install gnash but I can't get that to work.  I can't even seem to get the Gnash SWF Viewer to start.  
When I go to google video or youtube the adobe flash player is still starting so I assume that has something to do with my installing the package from adobe and not deb.(so I am having a hard time getting a clean de-install)
Just to be clear the video portion is fine but no sound.
If anyone has a any suggestions, I would be most appreciative.
Thx

---

### Post by philinux on 2007-11-20
Open the volume control prefs and make sure pcm is not muted or low level.

---

### Post by bwgolling on 2007-11-20
That is not the problem.  I checked and rechecked both with gui and cursers aumix.
tks

---

### Post by philinux on 2007-11-20
Ok so that avenue is eliminated.

Have you checked ```
about:plugins
``` in firefox.

Sometimes having more than one plugin can cause conflicts.

---

### Post by philinux on 2007-11-20
Found this, you dont say which version of gutsy you're running.
Anyway worth shot.

[http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)

---

### Post by bwgolling on 2007-11-20
Thanks for the effort but alas that did not do it either.
I guess if that's the only problem I have it will give me some goal to work for.  I have been playing around with linux long enough to know it always presents some sort of challenge

---

