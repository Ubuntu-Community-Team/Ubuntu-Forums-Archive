---
title: "Sound Skipping in VLC, Amarok, Totem, etc"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by LadyGodiva on 2008-02-23
Hello,

I am using Gutsy Gibbon (Ubuntu 7.10) for two days now. I have just converted, I am pleased with everything except this problem I have with audio playback.

Every audio player I tried starts fine then the sound starts skipping and gets stuck. I have to restart to get rid of this problem. I looked everywhere and installed all the suggested apps and whatnot, but nothing seems to be working. I have installed the Restricted Formats bit, too.

I should mention that when I start my Toshiba M55 laptop I hear the sound fine, and like I said, when I play music it starts normally then gets stuck. Sometimes I can play several songs fine and then they get stuck suddenly. I tried Amarok, Totem, VLC... same thing happens. The sound KEEPS ON skipping even AFTER I exit any audio players I have on. It's so strange!

My question is: if my soundcard is being detected (evidence: audio when I start Ubuntu), why is this happening? I am getting really frustrated with this. Any help would be very appreciated, thank you!

---

### Post by LadyGodiva on 2008-02-23
I want to add that this is not a problem with the Amarok, Totem, or VLC players. Because when I do the sound test from System--Preferences--Sound the sound plays AND gets stuck as well. Help! 

Damsel in distress here!!

---

### Post by Royajm on 2008-06-09
You could try typing "sudo -codec here- reload" in the command prompt, without the quotes and replacing the
-codec here- with the codec you're currently using like alsa etc. You could also try to uninstall the codecs
and then reinstall them a) from synaptic, using the players name as a searchphrase or b) doing it the command prompt way.
(I wont't go into detail here because there are lots of manuals for this)

One simple trick that I've picked up on the net is to shutdown firefox before playing any audio/video, since
the flashplugin might be stealing the audio but in your case I guess it won't work.

---

