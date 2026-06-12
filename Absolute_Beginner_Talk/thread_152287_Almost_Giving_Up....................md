---
title: "Almost Giving Up..................."
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-29
I have been trying to use my mic with ubuntu for almost three weeks now, and I just can't get it to work.
I have tried just about everything, including changing my volume control settings, alsa settings, then instaalled the so-called gnome sound-fix with automatix.  I just don't know what else to do! 
Yes I have tried with 2 different mics, both don't work. (one is just a mic and the other is a headphone/mic)
My sound card is a VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller, if that info helps.
My head phone works fine it's just the built in mic that doesn't.
And finally yes I have tried in Audacity to record stuff but even that doesn't work. :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by ajgreeny on 2006-03-29
I had problems with sound recorder not showing anything or playing back any recorded files.  If I shutdown sound recorder however, I got a dialogue asking to save file and if I did so, I could then play that file, so recorder did work.  Not much use though if you can't check more easily what is recorded before you save it.

I gave up and installed Audacity, which I've used before in Windows, and that worked a dream, so no going back.

---

### Post by user1397 on 2006-03-29
[QUOTE=ajgreeny]I had problems with sound recorder not showing anything or playing back any recorded files.  If I shutdown sound recorder however, I got a dialogue asking to save file and if I did so, I could then play that file, so recorder did work.  Not much use though if you can't check more easily what is recorded before you save it.

I gave up and installed Audacity, which I've used before in Windows, and that worked a dream, so no going back.[/QUOTE]
I tried saving it and playing it, but even that didn't work.  And audacity still won't budge!

---

### Post by siminone on 2006-03-29
In sound recorder, click on File then select Run Mixer Option.

This brings up the Alsa Mixer program. Click on Capture tab. I turned the volume right up and made sure it was not muted. I have a realtek AC97 card but Alsa is set to SIS SI7072 and it works fine.
 
Can you please confirm if this works. Not sure what audacity uses but I know that GStreamer does not produce sound output but xine does.

---

### Post by user1397 on 2006-03-29
[QUOTE=siminone]In sound recorder, click on File then select Run Mixer Option.

This brings up the Alsa Mixer program. Click on Capture tab. I turned the volume right up and made sure it was not muted. I have a realtek AC97 card but Alsa is set to SIS SI7072 and it works fine.
 
Can you please confirm if this works. Not sure what audacity uses but I know that GStreamer does not produce sound output but xine does.[/QUOTE]
No this did not work. Sorry! But do you have any other suggestions?

---

### Post by DeusEx on 2006-03-29
dumb question, did you select mic as source? and not muted it?

---

### Post by user1397 on 2006-03-29
[QUOTE=DeusEx]dumb question, did you select mic as source? and not muted it?[/QUOTE]
It's not muted but what do you mean select mic as source?

---

### Post by user1397 on 2006-03-29
Can someone with a working mic tell me their exact ALSA mixer settings please?

---

### Post by KansasJoe on 2006-03-29
Some mics are just set very low and you can't actually hear them (case with mine) type alsamixer in terminal and push right arrow until you get to the mic boost button and when you're on it hit m   may want to play with some other settings while you're on there

---

### Post by user1397 on 2006-03-30
Ah I figured it out! I ran the volume control and in preferences selected capture. Then I put capture all the way up and it worked!

---

