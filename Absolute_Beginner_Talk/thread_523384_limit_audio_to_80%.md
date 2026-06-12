---
title: "limit audio to 80%"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2007-08-11
is there a way to limit the audio output to say 80%....because after 80 it sounds distorted....no mater what my speakers are set to....like its distorted out of the line out of the soundcard

---

### Post by Skidpad on 2007-08-11
You could limit the output via Alsamixer.  Open a terminal and type "Alsamixer" (without quotes).  You can then raise/lower all of your individual volume levels.  Specifically, limit your PCM or Line volume.

---

### Post by notjohn101 on 2007-08-11
yes i no that but evey time i turn the sound down using my volume knob on my keyboard ...then go back up for wat ever reason i always go past 80 and then i have to find were 80s at and set it there....i want it for more of convenience then anything else

---

### Post by SirGrant on 2007-08-11
does your volume knob raise your PCM or your master volume.  I would find out which one it directly raises or lowers and then adjust the volume level of the one it does not effect to 80% via alsa mixer.

---

### Post by notjohn101 on 2007-08-12
bump

---

### Post by jimhaddon on 2007-08-12
why bump? you just had a suggestion!

---

### Post by Old Pink on 2007-08-12
Try dropping the PCM level. That didn't necessarily limit mine, but it fixed the distortion. Turn the volume to 100%, play something, and lower PCM until it's no longer distorted.

---

### Post by notjohn101 on 2007-08-12
sry i bumped probably as someone was writing that suggestion...ya no?

ummm i sould have made it clearer....it dont have a PCM or master or anythiung like that...the only fader in alsamixer or anywere else that controls the sound to my speakers is "anologe front"

---

### Post by fredj on 2007-08-12
Open the Alsa mixer (double click on the speaker icon in the taskbar) then use the
EDIT->Preferences menu to add all the possible volume controls and switches for both 
playback and record. Set suitable volume levels, close and reboot.

---

### Post by notjohn101 on 2007-08-13
no there is oither besides anologe frount to control my speakers

---

