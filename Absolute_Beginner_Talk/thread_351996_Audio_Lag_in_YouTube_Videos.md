---
title: "Audio Lag in YouTube Videos"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Gentex on 2007-02-02
I noticed something odd last night while browsing around YouTube.  While running Firefox under Edgy, all of the videos I watched had an audio lag of about 1-2 seconds (meaning the audio was a second or two behind the video).  The same videos in Firefox running in WinXP didn't have a lag.  Is this a common issue?  Is there any way to fix the "problem?"  Or, am I the only one to notice something like this? 

Gentex

---

### Post by RomeReactor on 2007-02-02
It seems you don't have Flash 9. Go to [Adobe's]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW") page and download the .tar.gz file (option 1); close Firefox, open Nautilus and got to "/home/USER/.mozilla/plugins" and delete "libflashplayer.so". Extract the file and copy **that** libflashplayer.so to the plugin folder. **Or** just use the installer: In a terminal, change to the extracted directory and then type

```
sh flashplayer-installer
```

Restart Firefox.

---

### Post by Gentex on 2007-02-02
Good point Rome.  I didn't check that.  Thanks for the suggestion.

---

