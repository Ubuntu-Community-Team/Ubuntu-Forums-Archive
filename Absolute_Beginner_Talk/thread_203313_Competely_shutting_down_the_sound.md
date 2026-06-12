---
title: "Competely shutting down the sound"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-25
My laptop, Dell Latitude, is older, and it has a faulty audio controler.  Half the time when I boot I get a solid lock up at "loading hardware modules."  Anyway, I want to completely shutdown sound.  I need the resources anyway, and it will stop locking up rigth?

How do I do this, and where do I go to comment out modules that have to do with sound?

---

### Post by WADemosthenes on 2006-06-25
Could I just comment out the audio part of my xorg.conf?  Then, where can find the modules list that I can edit?

Edit: that was a stupid idea (I didn't do it), I found that you can blacklist modules, and everthing seems to work well now.  Sound it not working now, which is a good sign :P  I black listed snd-nm256, does that sound right?  Anyway, as long as I'm junking sound are there any other modules that I can black list in order to speed up boot?

---

### Post by linuchsan on 2006-06-25
The fastest way would be to disable it in the bios.

---

### Post by WADemosthenes on 2006-06-25
How do I get into the BIOS?

---

### Post by linuchsan on 2006-06-25
Press F2, when you boot the laptop

---

### Post by acht on 2006-06-25
[QUOTE=WADemosthenes]How do I get into the BIOS?[/QUOTE]
 lol sigged

f2 or delete

---

