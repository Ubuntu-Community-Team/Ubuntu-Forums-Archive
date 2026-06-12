---
title: "[SOLVED] no sound firefox"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by just learning on 2007-05-22
i can't seem to get sound in firefox or epiphany when playing video on a site. i installed flash player via terminal but i don't know how to check if it's being used.i got no errs during install.
i get sound every where else.help please:(

---

### Post by Kobalt on 2007-05-22
Are you trying to see a streamed video in 'video' format (windows media, realplayer, etc.) or a flash format ?
Have you installed the [audio/video codecs]("http://ubuntuforums.org/showthread.php?t=413624") ?

---

### Post by Sparkster185 on 2007-05-22
To see what plugins are actually install in Firefox, in the URL bar type "about:plugins".  If you're able to view videos, etc. then I bet you have it installed correctly.

I used to have this problem, but Feisty seemed to fix it for me.  What I used to have to do is close all applications that use sound (AmaroK, etc.) and restart Firefox.  Try this and see if it works for you.

---

### Post by just learning on 2007-05-22
i checked for all the codecs and i have them and flash. it seems to only happens on some of the sites prob. diff. format right. i think it maybe be streaming video.

---

### Post by Sparkster185 on 2007-05-22
So the sound works on some sites and not others?  Do you know which formats are causing it to break?  If it's simply Flash, your sound should work.  I know there are ways to get .wmv and Quicktime to play in Ubuntu, but I haven't done it.  I'm sure you can find it with a little searching.

Have you tried using Automatix to install codecs?

---

### Post by just learning on 2007-05-22
it's just music videos, i right clicked the video and a flash settings came up so i guess it's flash format?

---

### Post by irish_flu on 2007-05-22
This page has a little flash thing on it so you can test your sound in flash:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

and this page should also tell you whether or not flash is working properly (this page doesn't have any sound, though):

[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

---

### Post by just learning on 2007-10-09
problem fixed i had to go into my cmos and disable my onboard soundcard. once i did that blamo everything worked, i have two sound cards i don't use my onboard.thanks for all your help folks.

---

