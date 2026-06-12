---
title: "[SOLVED] internet videos and music won't play at hte same time"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Darkade on 2008-04-04
Hello, I'm using the Hardy beta and I've been having some trouble with it. What happen is that whenever I'm hearing to some music or video in say Rhythmbox or Totem internet videos like google videos, or youtube, or pretty much any other video of that streaming kind it won't play. It will load (in youtube I see the progress bar filling up) but it just won't play. I can only fix this by closing the other app and restarting firefox. I don't know why it is but it all started when I upgraded to Hardy Beta, so my best guess it's that it is the new "Pulse Audio" and I really don't know how that works. Any Ideas? Am I the only one with this problem? Or, in case it is a bug, do you know it it will be fixed in the final realese?

By the way, Hardy works pretty smooth for any other thing I've tried so give it a shot :D:D

---

### Post by scrime on 2008-04-06
Maybe you need to install codecs? [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by briguyd on 2008-04-24
I have the same issue. Anyone else experiencing this?

---

### Post by Darkade on 2008-05-09
I got it solved. Goto to
   System>Preferences>Sound
and make sure you have
PulseAudio Server selected in all of the options
now, open a Synaptic and install libflashsupport this enables playing flash audio using PulseAudio.
It's kind of buggy if you click the "back button" in firefox (in fact it's a confirmed bug), but for every other matter it works fine.

also you should install

libflashsupport

that's the library to play flash with PulseAudio

---

