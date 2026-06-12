---
title: "G4 PPC/Jaunty audio level low"
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-09
I have Ubuntu 9.04 running on my old Sawtooth G4 450 mhz and everything is working, although I notice the volume when I play mp3 or other audio files is considerably lower than when the same computer is running OS X. Is this normal? I have tried to find all the volume sliders and made sure they were up to the maximum but it's just much lower than I'm used to. I have a lot of pro audio gear here and even a second G4 and the difference is about 15-20 dB, I'd guess. Using the input knob on my Mackie 3204 I have to set the volume level to 3PM for the Ubuntu machine while the same computer under OS X would be set to 10AM - big difference.

I am using Rhythmbox and I've also tried Movie Player.

It's okay if this is normal (well, I'm not delighted), but it would just be nice to know if this is what I should expect.

Thanks!

---

### Post by stream303 on 2009-05-10
Doublecheck that in addition to the main volume slider for say Gnome, you also have the sliders up in the sound application itself as well.

Also be sure to check your PCM and speaker levels with ALSAMIXER - once you set these here, your gui controls should have more range.

In a terminal, fire up *alsamixer*

Then use the space bar and up/down arrow keys to adjust levels.  If you find a channel muted, you can toggle it with the M key.  You can also balance them with the B key if you find a stereo pair out of balance - and then again use up/down to adjust overall level.

Be sure to use the TAB key to be able to see all the channels available to you.  When you are done setting levels, hit ESC to get out of alsamixer.

I normally recommend bringing the PCM levels down about 3 to 6 db from maximum at least, and then move on to the speaker channels - usually around 75% or perhaps -10 db.  THEN go back into the gui sliders and see if you now have a more comfortable range.

---

### Post by Benboom on 2009-05-10
Yes! That seems to have resolved it. I've posted a full response in the other thread, along with the info you asked for. Thank you very much!

---

### Post by AussieHolden on 2009-05-10
This has not worked at all for me my system has no sound at all and no fix to it yet.

---

### Post by stream303 on 2009-05-10
AussieHolden:

We still don't know what your system is.  (unless I've missed it elsewhere).

Thing is, the Ubuntu devs don't read this forum, so they are missing your requests to fix the bugs.

About the only thing you can do at this point is go back to the previous system that worked, try another distro, or roll up your sleeves and become a geek like us. :)

---

### Post by hotani on 2009-06-12
I know exactly why my sound is low, but as of yet am unable to do anything about it. When using 8.10, my volume control was set to PCM. Now I found that the system volume keys access Main instead, so I went to change the volume control and there is no PCM!

alsamixer returns: alsamixer: function snd_ctl_open failed for default: No such file or directory

alsamixergui opens but there is still no PCM. I have Main at 100% but PCM is stuck at 20%. 

I never understood why there were 2 separate ways to control volume, but oh well. It seems consolidated now, but only halfway. Any way to get access to PCM again?

---

