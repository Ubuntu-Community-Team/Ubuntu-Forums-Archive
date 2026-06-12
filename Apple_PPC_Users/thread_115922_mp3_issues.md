---
title: "mp3 issues"
date: 2006-01-11
forum: Apple PPC Users
---

### Post by lunatic77 on 2006-01-11
I have installed Ubuntu/Kubuntu on my PowerBook G4 and almost everything works wonderfully.  I still cannot get mp3's to play, however.  After doing some research, I have installed libgstreamer0.8-mad (and a handful of other libs), 
uninstalled and re-installed amaroK several times, and I am still having problems.  

Specifically, the error message in amaroK (or any other player, for that matter) is something like "mad0: failed to negotiate" (I don't remember it exactly since I don't have my machine right here).

Any help would be greatly appreciated!

---

### Post by Neo Ex on 2006-01-11
After you install gstreamer0.8-mad, run 'gst-register-0.8'.
Then, install the Xine engine for amaroK (amarok-xine) and use it instead of the GStreamer engine.

---

### Post by ajgreeny on 2006-01-11
Try adding lame, liblame0, and gstreamer0.8-lame with synaptic.  I have all these installed and can both encode audio to mp3 and play mp3 in all my audio player progs without any problems.

---

### Post by lunatic77 on 2006-01-12
[QUOTE=Neo Ex]After you install gstreamer0.8-mad, run 'gst-register-0.8'.
Then, install the Xine engine for amaroK (amarok-xine) and use it instead of the GStreamer engine.[/QUOTE]
I installed xine exactly as you said and it works perfectly.  Thanks!!!!

---

