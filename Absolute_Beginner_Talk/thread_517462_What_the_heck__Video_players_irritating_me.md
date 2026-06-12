---
title: "What the heck?  Video players irritating me"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-08-04
Okay, I have several movie players on ubuntu now and I've had to install all of them because everyone keeps telling me I need this one or that one to play such and such video.

And I'm really starting to get irritated with it all.  All I want to do is play wmv files and that's it.  And some of the programs play the video in the file but not the audio, but then another program will play the freaking audio but no video.

So what am I supposed to do?  I have all the codec packs installed that every guide on the planet tells you to install.

I have gxine, it'll play the audio, but then the video is scrambled
Movie Player will play the video but no audio
Smplayer and mplayer will play audio and no video.

Wmv is one of the most popular formats out there and most web sites these days encode their downloadable video in wmv format.  

Is there someone out there who can actually guide me to being able to play this format's audio and video?

---

### Post by happy-and-lost on 2007-08-04
Have you tried VLC? I'm not a huge fan, but it does play everything I throw at it without kicking up a fuss.

---

### Post by pete83 on 2007-08-04
And I AM a fan of VLC. I agree to use VLC. It will work. If at first it seems not to work, then go into the settings>>preferences>>video>>output modules  (or audio>> output modules) and try a different module until you find the one that works on your system. You will need to check the "advanced" box to see the modules. On my computer, I use the alsa audio module and the opengl video module.

---

### Post by dasunst3r on 2007-08-04
It sounds like you are missing the package *w32codecs*.

---

### Post by RudolfMDLT on 2007-08-04
> **dasunst3r said:**
> It sounds like you are missing the package *w32codecs*.

I agree:

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

If you have installed them then redo so.

And here is another  - kaffein!  looks prettier than vlc and plays very well! And yes - the codecs thing is a issue! :) hang in there!

---

### Post by CryptiniteDemon on 2007-08-04
Well I reinstalled my w32codecs.  

Works in gxine only now.  None of the other programs work for both the audio and video.  Still the audio sync is crappy.  Both on HD and low res files.  

I can't get the audio to work in VLC.  I tried every setting in it and nothing makes the audio play at all.

---

