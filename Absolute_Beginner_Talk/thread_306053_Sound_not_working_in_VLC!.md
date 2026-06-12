---
title: "Sound not working in VLC!"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by unbuntu kid on 2006-11-24
After getting the plugins for the default GNOME media players to play mp3's (and ending up in visualizaions working but no sound) I tried VLC's media player and recieved the same results.

Is there some kind of line of code I hve to edit to enable sound in medai players.

PS Firefox sound works and so do login sounds.

---

### Post by livinginx on 2006-11-25
Open up VLC, the click on "Settings > Preferences"
In the bottom right corner, click on "show advanced options"
Now, expand the top left menu "Audio"

Go down and expand "Output Modules" but click on it.  Make sure it is set to either default or whatever sound driver you prefer ALSA or OSS
If you use alsa at all, click the left column where it says ALSA
Then in the right pane, click on refresh list.  Then select one of the options in the drop down list.  Mine lists 2 -=- hw0,0 and hw0,2
One is for headphones/analog the other is for the Optical spdif.
Click save when you are done (make sure nothing is playing.)

Also, if you are playing a video/dvd check your audio device from the "Audio" menu.
Hope it helps

---

