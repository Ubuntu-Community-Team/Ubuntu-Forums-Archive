---
title: "Playing a Real Video 3.0 / Real Audio G2 (Cook)"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-28
I was wondering how I can play Playing a Real Video 3.0 / Real Audio G2 (Cook) on Totem Media Player?

---

### Post by gobbles414 on 2007-08-28
Hi amitroy5,

The first thing you should do is visit the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") page at the Ubuntu Documentation Community Docs.

* Install w32codecs (once you've enabled Medibuntu you can do this using either the terminal, or the Synaptic Package Manager. **Other things to consider doing:**

* Replace the gstreamer version of Totem with the Xine version of Totem. This will enable you to access DVD menus in Totem. You can also add the libxine-extracodecs to further enhance your experience.

* Install VLC as an alternative for the files Totem may not be able to play. 

* Replace the Totem plugin for Firefox with the MPlayer plugin. Totem in Firefox is not the best option.

* There are a class of packages called gstreamer0.10. It is worth your time to explore these. 

* Activating Medibuntu will also give you access to the official version of Adobe Reader (and various PDF-related plugins)

* The Ubuntu-restricted-extras package is also worth installing, IMHO.

---

### Post by amitroy5 on 2007-08-28
I have installed all those packages. Like, I can play DIVX and MP3 files in Totem. However, I cannot properly play real video files.

Also, VLC player cannot play real video files. On top of that, it cannot play files though Samba. Is there anything else I can do?

---

### Post by gobbles414 on 2007-08-28
amitroy5,

Could you use the Real Player in the Medibuntu repository? Maybe the Helix player...? Please keep me up-to-date on your progress!

---

### Post by amitroy5 on 2007-08-28
I have tried Real Player, but its very choppy. I decided that it would be best to figure out a way to convert it to another format.  Real player formats aren't that linux-friendly.

---

### Post by gobbles414 on 2007-08-29
amitroy5,

mencoder is supposed to be a good conversion engine. And, I believe that there are lots of programs in the repositories that use mencoder as their foundation.

---

### Post by gobbles414 on 2007-09-01
amitroy5,

How are you progressing?

---

### Post by amitroy5 on 2007-09-01
I just went on Windows and converted the format to DIVX using the DIVX conveter utility.

---

### Post by gubemton on 2008-01-12
I've had a similarly unsatisfactory experience with RealMedia 3.0 (from the BBC)

RealPlayer 10 shows video but doesn't play audio.

HelixPlayer tells me to go away: "The player does not have the capabilities to placy back this content. This content is supported by RealPlayer" 

VLC (which doesn't handle RealMedia) reports it can't open the URL in the .ram file (but doesn't say it can't play Real)

While Xine doesn't play the content, it at least offers some helpful error messages, viz    

"A problem occured while loading a library or a decoder cook.so"
"A problem occured while loading a library or a decoder drvc.so"
(The "More ..." button provides additional information)

Now at least I know that I need to get RealPlayer 10 to use the cook audio codec to play RealMedia 3.0

---

