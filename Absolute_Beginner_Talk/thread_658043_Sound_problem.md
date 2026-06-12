---
title: "Sound problem"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by William S on 2008-01-04
Hello!
I have a little problem with my sound in Ubuntu. 
Everything works fine except playing the sound from videos in Youtube (Ubuntu 7.10) 
And yes the Youtube volume control is on full. I  try the same thing in Slackware and it works in Youtube.

---

### Post by NilsE on 2008-01-04
See what version of the flashplugin you are on.  You may have to upgrade for the sound if you are on 48.

On the url line Firefox enter about:plugins and let us know what it is.

If you have to upgrade search on flashplugin since there may still be a problem with 115 in the repositories.

---

### Post by William S on 2008-01-04
Yup it said I am on 48. Now what to do?

---

### Post by NilsE on 2008-01-04
Instructions are at the top of the following thread.  There is both a 32bit and 64bit deb file you can use to install.  First remove the old version via synaptic then download the deb file and follow the instructions to install it.

[http://ubuntuforums.org/showthread.php?t=636397&highlight=flashplugin](http://ubuntuforums.org/showthread.php?t=636397&highlight=flashplugin)

---

### Post by William S on 2008-01-04
Still didn't work...

---

### Post by NilsE on 2008-01-04
> **William S said:**
> Still didn't work...
Did you remove the old one first?

Did you install the correct one for your OS (32 or 64)?

Did you close all Firefox windows during the install?

In other words how did you install it.

---

### Post by William S on 2008-01-04
I did remove the old one completely, then downloaded the correct .deb file and installed it and Firefox was closed.

---

### Post by NilsE on 2008-01-04
Seems odd that everything else is fine and only a problem with YouTube audio.  

Try this flash video and let me know how it works. Sound and Video.

[http://www.albinoblacksheep.com/flash/numa](http://www.albinoblacksheep.com/flash/numa)

---

### Post by William S on 2008-01-04
It seems to be a problem in general with sound on Flash movies in general, because the sound here didn't work either.
Video worked fine though.

---

### Post by NilsE on 2008-01-04
Try this just in case your config file is corrupt

mv ~/.asoundrc .asoundrc.junk
mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.junk

Then restart Firefox


If that does not work here is some more info on how to fix the sound problem with flash

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

---

### Post by William S on 2008-01-07
Hey thanks for all help Nilse, the last package helped. :)

---

