---
title: "mp3/sound trouble"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by efplaya21 on 2007-05-22
Hi i just installed all those codecs and drivers from the restricted sites to get my dvd working, and thankfully that works now, but now i'm having a little bit of distortion while playing mp3's, does anyone have this problem, is there any solution?

---

### Post by squinx22 on 2007-05-22
Did you install VLC media player? If not, try installing it from the synaptic... search in VLC

---

### Post by efplaya21 on 2007-05-22
but i listen to music on amarok and i kind of like the program does that jsut mean i cant listen to amarok anymore since i cant fix this very mildly distorted sound

---

### Post by efplaya21 on 2007-05-22
i also have a distorted sound on exhaile which means it is probably on all of my media playback for mp3s

---

### Post by zvacet on 2007-05-22
> Amarok folks pay attention to this: if you use libxine-extracodecs together with gstreamer0.10-plugins-ugly installed, the sound of playing mp3 will become weird. Simply remove gstreamer0.10-plugins-ugly.

Is this of any help?

[https://help.ubuntu.com/community/RestrictedFormats/MP3]("https://help.ubuntu.com/community/RestrictedFormats/MP3")

---

### Post by efplaya21 on 2007-05-23
i just did that and it still plays distorted for some reason

---

### Post by Voland on 2007-05-23
Have you tried different players like rhythmbox or another?

---

### Post by efplaya21 on 2007-05-23
yes exhaile is also having distorted sound...

---

### Post by efplaya21 on 2007-05-23
and the sound is fine during dvd or cd play... wierd

---

### Post by JPorter on 2007-07-21
First, make sure you are using the ALSA mixer by checking your settings in System > Preferences > Sound.

Then, run alsamixer by opening a Terminal and typing

```
alsamixer
```

You will see a bar equalizer.  Take note of the gain settings on PCM and (possibly) CD.

**Lower the gain on all channels other than the master volume to 0.00db.**  This should be 3/4 of the way up or so.  The critical channel in this case is PCM.  

You also may want to turn the Microphone setting all the way down, sometimes certain sound cards create an open loop to the mic and distort that way, too... but it sounds like you're having a simple gain issue.




Now, go back and have a listen.   Is it fixed?

If so, save your alsamixer settings by typing

```
sudo alsactl store 0
```

If you have more than one sound card, you may need to set the "0" above to another value accordingly.

---

### Post by bengoza on 2007-10-11
Thanks for the help with alsamixer, it sounds better now, but it always sounded okay in XMMS--what's up with that?

---

### Post by hoggbottom59 on 2008-02-15
I have the same problem in everything but Exaile.

So for a while I've only used Exaile but now that's gone t*ts up!

Leon.

---

### Post by kesomir on 2008-02-15
try dropping the master volume down from 100% until distortion dissappears.

---

### Post by Bubba64 on 2008-02-15
The 3D depth in the volume control on some songs if turned up all the way causes some distortion in the bass.

---

