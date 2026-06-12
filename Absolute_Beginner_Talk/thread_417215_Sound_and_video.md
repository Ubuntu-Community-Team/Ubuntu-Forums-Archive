---
title: "Sound and video"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-21
For some reason I can't hear anything or see video. When I open a video and drag the window I can see what's playing, it's really weird.

---

### Post by Campingman on 2007-04-21
What player are you using?  Are desktop effects or Beryl enabled?  Is it the same in different players?

---

### Post by Biscuitpie on 2007-04-21
Well, the sound isn't just players. And I only tried the movie in the default one (totem?). I am running Beryl, but I tried it without Beryl and the same thing happened.

---

### Post by Campingman on 2007-04-21
I have had an issue with the video in all players with Beryl enabled and wondered if it could have been part of the same problem.

---

### Post by Biscuitpie on 2007-04-21
No idea, but this is pretty important.

---

### Post by Biscuitpie on 2007-04-21
Anyone?

---

### Post by Biscuitpie on 2007-04-21
I seriously need sound. :(

---

### Post by Biscuitpie on 2007-04-21
:( Please?

---

### Post by Kougaiji on 2007-04-21
I'm having the same issue with 7.04. I fixed them back in Edgy, but now I gotta start all over again?

---

### Post by Biscuitpie on 2007-04-21
I could hear in edgy and feisty, just stopped working today.

---

### Post by Happy_Man on 2007-04-21
So, you could hear in Feisty before today?

---

### Post by Biscuitpie on 2007-04-21
Yep. Dunno if it was before or after installing beryl. But when Beryl is off, nothing changes.

---

### Post by Biscuitpie on 2007-04-21
Nobody knows at all? Wow, this sucks. >.<

---

### Post by Biscuitpie on 2007-04-22
Aha, I have located the problem as Beryl, so you were right. Anyone know what to do?

---

### Post by Happy_Man on 2007-04-22
Well, if you know the problem, why don't you fix it?

---

### Post by Biscuitpie on 2007-04-22
Because I don't know how?

---

### Post by Happy_Man on 2007-04-22
Oh, yeah, right, sorry!:redface: In any case, what did Beryl do?

---

### Post by Biscuitpie on 2007-04-22
I fixed sound via alsamixer. I don't know what it did, but I just can't see videos. They're black. If I move the window around and let go, I see a flash of the video. =/

---

### Post by Biscuitpie on 2007-04-22
:(

---

### Post by Happy_Man on 2007-04-22
There is no real fix for that, just restart the program and the video should come up. I had the same problem, and that was how I fixed it.

---

### Post by Biscuitpie on 2007-04-22
It doesn't matter what I do, I've tried "Movie Player" and VLC. Both are like that. It was only like this after installing Beryl, and I never had to turn Beryl on for it to stop working.

---

### Post by Campingman on 2007-04-22
Hi,

This sound like the problem I and a few others have had with desktop effects and beryl enabled. 
Have a look through this thread and try the different setting adjustments
[http://ubuntuforums.org/showthread.php?p=2493353&posted=1#post2493353](http://ubuntuforums.org/showthread.php?p=2493353&posted=1#post2493353)

Hope it works for you

---

### Post by Campingman on 2007-04-22
These two did it for me
In terminal
$ gstreamer-properties
In video tab I changed the plugin setting to X window system (no xv).  This sorting out Totem

In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC.

These two sorted out my video issues, I hope they do it for you.

---

### Post by Biscuitpie on 2007-04-22
Great, those both work. Thanks! :)

---

### Post by Campingman on 2007-04-22
No problem, sort of threw me yesterday as you had a sound problem as well I did not think it was related.

---

### Post by XenSA on 2007-04-27
Thanks Campingman i just started having the same problem after 2days of the video working fine??!!!

and your fix worked first time


thank you

---

### Post by kittyhawk63 on 2007-04-27
Just saving this thread.
kh

---

