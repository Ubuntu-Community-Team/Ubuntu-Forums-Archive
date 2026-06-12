---
title: "re: Audio stream volume"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by vnzjunk on 2007-03-12
Hi

I have a question about playing audio streams.  My system brings up the totem movie player to play the streams and they do play.  However the volume at max is about half of what I was used to under windows.  I have the volume of the external speakers as well as the slider on totem all the way up.  Is there a 'master' volume controll in one of the multi media settings available to turn the volume range up?  

Also, is there another player available that is more suited to audio streams.  Maybe one with a graphic equalizer that someone might suggest.

Thanks

vnzjunk

---

### Post by dptxp on 2007-03-12
I too have low volume problem with UBUNTU-6.10 (64) on my ACER 5101 laptop. This may not be right place (this is for documentation of UBUNTU), but I gather that there can be a section in documentation on AUDIO drivers, problems and solutions.
:guitar:

---

### Post by bapoumba on 2007-03-12
@ vnzjunk: thread moved to "Absolute Beginner Talk" support forum.

---

### Post by dptxp on 2007-03-12
I have another problem (Realtek Audio). The audio works on one channel only. But if I open the volume control, press (click) the 'mute" twice (mute and then disable mute), I get sound on both channels. (laptop, acer 5101, 64 bit Ubuntu 6.10).
:guitar:

---

### Post by docshawnc on 2007-03-12
You might give this a try:  go to a terminal and type 'alsamixer' (no quotes).  This will open up a mixer console where you can try setting everything to max.  Of course if you're not using alsa for you sound, it won't work for you.

---

### Post by vnzjunk on 2007-03-12
Docshawnc

Thanks for the answer.  I did go into terminal and typed alsamixer.  It brought up a nice graphic panel but none of the settings seemed changeable from the interface.  Also I am not sure if this interface is at all connected with the totem player or not.

vnzjunk

---

### Post by docshawnc on 2007-03-13
Did you try using the up/down/left/right arrow keys to make adjustments?  Hit escape when finished to save your new values.

---

### Post by Archmage on 2007-03-13
Right click on the volumeicon in the gnome pannle - than go to configure volume. There you should find out that beside the master volume you also have to set the PCM volume.

---

### Post by vnzjunk on 2007-03-13
That did it.  I forgot about the keyboard controls.  But I am catching on.  Now have volume a plenty, in fact I am pretty sure that I never heard that kind of volume out of the windows controls although I had plenty of volume to spare there.  This may be a good thing...........for the speaker resale people <grin>.

Again thanks for the obvious, which isn't so obvious to us newbies.....

Mark

---

### Post by vnzjunk on 2007-03-13
Any suggestions for a program which gives graphic equalizer controlls to audio playback?  I have the real player installed.  Not sure if I did it as a plug in for Firefox or stand alone, but I have the streams playing through it.  I know the more advanced win real player had an equalizer included but not this one.

Any and all suggestions will be appreciated.

Thanks........Mark

---

