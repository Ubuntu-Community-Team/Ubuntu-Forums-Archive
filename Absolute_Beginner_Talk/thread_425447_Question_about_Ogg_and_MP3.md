---
title: "Question about Ogg and MP3"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-04-27
Kinda a question from my curiosity. Is there a linux program that allows easy batch audio conversion, specifically MP3 to Ogg, and reverse.

---

### Post by madmetal on 2007-04-27
sudo apt-get install mp32ogg

then move to your music folder  and give..

mp32ogg --delete *.mp3

to convert mp3s to ogg..

If you want to convert to ogg and KEEP your mp3 files too, do this

mp32ogg *.mp3 

(searching the forums and find it here.. 
[http://ubuntuforums.org/showthread.php?t=261114](http://ubuntuforums.org/showthread.php?t=261114) )

---

### Post by starcraft.man on 2007-04-27
Thanks mad metal, sorry forgot to search. Hehe, will do next time.

---

### Post by dreadlord_chris on 2007-04-27
Do you realize that converting from one *lossy* format to another can **only** result in degraded quality?

---

### Post by Josey on 2007-04-27
I started to do the same thing with my music collection when I first started ubuntu but .ogg and my ipod don't like each other so for now it's mp3 for me I guess.  :(

---

### Post by viciouslime on 2007-04-27
> **dreadlord_chris said:**
> Do you realize that converting from one *lossy* format to another can **only** result in degraded quality?

Yeh, but seriously, try it on one file and I think it is incredibly unlikely you will be able to tell. You have to convert between lossy formats many times before the vast majority of people have any idea of sound degradation.

You might want to look in to "sounds converter" it's in the repos and can be installed via synaptic or add/remove applications. This will give you a nice gui, makes things much easier if your files are in numerous folders!

Plus it is written in python so really easy to edit if it won't do exactly what you want.

---

### Post by starcraft.man on 2007-04-27
Thanks vicious slime and yes dreadlord I do know that converting more often than not degrades the quality of whatever you convert. It usually isn't that noticeable as pointed out.

---

### Post by RedSquirrel on 2007-04-27
**audacity** is another one in the repos (it has a GUI).

---

