---
title: "Sound Doesn't Work"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by PoisoN2003 on 2007-05-23
Any ideas what i could do to get my sound working 
I have a SB live 5.1 and i get no sound what so ever i checked the prefrences->sound and checked my sound card but still nothing

---

### Post by BobLand on 2007-05-23
Try this:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Make sure you reboot.  Go to System/Preferences/Sound and run all of the sound tests.  Make sure your driver is displaying.  If your driver is not in the drop downs, run the above procedures again.  

After a while if you find no sound again run these commands:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

On my system - Sound Blaster Audigy LS, if I don't run the last line I loose the gui.  Make a note of that line and stick it somewhere where you can find it.  On the other hand, if you get stuck at the command prompt and don't have a clue why, type:
**gdm -help**.  The system will tell you what to do.


Run a search.  You'll get hundreds in not thousands of hits, all of them good.

bobland

---

### Post by PoisoN2003 on 2007-05-23
i tried both things still wont work

---

### Post by PoisoN2003 on 2007-05-23
bump....

---

