---
title: "Very Quiet volume"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Sugz on 2008-03-21
When watching media on my laptop, the maximum volume is very quiet, is there a way to override the volume setting so it is louder, similar to a macbook? 

THanks in advance
-Sugz

---

### Post by billgoldberg on 2008-03-21
Open up a terminal and enter:

```
sudo apt-get install gnome-alsamixer
```

Then go to "applications -> sound and video -> gnome alsamixer"

Max out the voumes there.

You could also just enter "alsamixer" but that is a bit more difficult to use.

---

### Post by Sugz on 2008-03-25
Thank you for that suggestion. but the volume is still rather quiet. I had used those settings in the default sound and volume manager earlier (i should have said that) 
Mind the volume was more or less the same back when i was using Vista on this laptop, would this be a hardware limitation and not a software limitation?

---

### Post by hyper_ch on 2008-03-25
I think you need to volume up the PCM

---

### Post by Bri0 on 2008-03-27
Using headphones its the same for me aswell (Realtek ALC888 - ALSA), even with PCM at its max. On Windows it can go way up.

Normal master volume % for me
In Win: 20%
In Ubu: 58%

When I installed ubuntu on a older system that had a old 'Creative Sound Blaser Live' card the volume was louder then that of what I have now.

Guess that's the way it is. I have gotten used to it now, tho it could very much be better.

---

### Post by which_chick on 2008-03-27
My laptop sound got a lot better when I jacked the sound for "front" instead of just the PCM thing.

   1. Right click on speaker icon in system tray, and select "Open Volume Control"
   2. Go to Edit: Preferences
   3. Put a check next to Front. Hit OK
   4. Turn Front volume all the way up.

I don't know if it will help you or not, but it's an easy thing to try.  My laptop is now loud enough to scare the cats.  :)

---

### Post by alejo0823 on 2008-04-07
I have the same problem I have a Realtek ALC888 integrated sound in my board, in windows the sound its really good and loud but in ubuntu its very low. Its there a file you can edit to get more volume?

---

### Post by SlappyPappy on 2008-04-07
I had the same problem listening to a DVD last night but you can double click on the volume and a mixer comes up. Jack up the PCM and you should be good to go.  :guitar:

---

