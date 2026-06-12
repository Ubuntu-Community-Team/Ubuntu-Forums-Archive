---
title: "Tovid Background Music"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Nazty_Nayt on 2008-02-13
Just got a couple of quick questions.  For tovid, is there any certain type of file I have to have to set up background music (mp3. wav, midi, etc...), and does it have to be a certain length?

---

### Post by yabbadabbadont on 2008-02-14
Which tovid program are you trying to use this music with?  todisc, makemenu?  Which version of tovid are you using?

Edit: I'm going to assume that you are talking about the "-bgaudio" option with todisc.  Looking at the code, it appears that you can use any audio file type that mplayer can play.  You may also want to be sure that ffmpeg can play it too, as ffmpeg is used in some cases instead of mplayer.

Edit2: The length of the audio file should be as long, or longer, than the playtime of your menu.

---

