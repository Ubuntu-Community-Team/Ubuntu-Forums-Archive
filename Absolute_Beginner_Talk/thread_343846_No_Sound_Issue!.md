---
title: "No Sound Issue!"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by brandknewme on 2007-01-22
Hello,
I have installed Ubuntu and everything was working fine.  Suddenly, I have no sound, it worked for a week or so. I'm not sure why. 
When I go back into windows, I have sound there and it works fine. Just not in Ubuntu.


Can you please help me out? I love my music and I don't want to be forced to use windows just so I can hear my tunes *L*

---

### Post by Shutdownrunner on 2007-01-22
I know it's a bit too simple piece of advice, but are you getting any error messages when trying to play music? If not this means that sound driver is loaded and working, but you need to use some mixer and turn volume up a bit. In my case e.g. master sound control is called headphone. No idea why, but main just doesn't work. I have no problem with it. I just had to get used to it. 

Try to play with your mixer and if this doesn't help we'll try to apply some more sophisticated methods.

---

### Post by tommcd on 2007-01-22
First the easy stuff. Type alsamixer in terminal. Scroll right to left and turn the volume for everything up (use the arrow keys). Then click system>preferences>sound, and make sure it is set to ALSA, and click on the 'test' buttons. If still no sound, then try working your way through this:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

