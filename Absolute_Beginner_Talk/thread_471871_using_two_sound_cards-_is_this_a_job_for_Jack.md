---
title: "using two sound cards- is this a job for Jack?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-12
I have an onboard sound that ubuntu picked up on install (feisty), configured happily with ALSA. There is also a soundblaster audigy platinum card installed, which I don't think the o/s noticed because I can't find any reference to it anywhere. 
I think I want to activate both, because I need to listen to a CD and record from other input sources at the same time.  Is this possible? Can I install two sound cards? How can I instruct ubuntu to notice the soundblaster without forgetting about the onboard sound, and is Jack the best thing to use to mix them all together?

---

### Post by Sloddy Shipper on 2007-06-13
Hi, you should be able to do this without using both sets of sound hardware. AFAIK trying to use onboard sound and a separate soundcard is not likely to work very well if at all. Although i've never used it i understand jack to be for sending audio between applications and not really concerned with hardware, (like rewire in windows i think).

So, for what you want to do, (record other sound source while listening to a cd), you need to select the correct record source in the ALSA mixer.  Lets say you want to listen to the cd mixed with the line-in signal (from your other sound source), but only record the line-in. Set the appropriate listening levels in the playback mixer but only enable recording for the line-in. 

How you enable recording may vary depending on your hardware so you may have to hunt about in the mixer preferences.

If you prefer to use the audigy for its quality/features, you most likely need to disable the onboard sound. This can probably be done from your BIOS setup or (if you're unlucky), a motherboard jumper. Reboot after you have disable this and with luck the audigy will be installed automatically. This worked for my SBlive. Hope this helps.

---

### Post by Aliby on 2008-01-14
I have installed UbuntuStudio 7.10.
I also have an on board sound card and, in my case, a SoundBlaster Live.

If I go to my mixer I can see and select either of the cards for playing audio, and similarly for recording.
I am trying to be able to access both cards so I can record from both cards simultaneously ... this still waits to be seen.

ANyone else got ideas, tried this or got it working?

:)

---

### Post by zettberlin on 2008-01-14
Listening to something and recording something else is no problem with jack. Compile/get Xinelib with jack-support and use xine to listen to the CD and Xine shows up in qjackcontrol as a seperate port you can connect as thou wishest...
To record from the soundcard at the same time connect alsa_pcm_capture to the input of the recording program (e.g. Ardour, timemachine, mhwaveedit you name it).

Regarding multiple soundcards:

jackd can only connect to a single alsa/freebob-port at a time. This is deliberate and will not change for jack is made for pro audio and proaudio and 2 different clock sources in one setup is contradictionary. It is whatsoever possible to simulate something like a multichannel soundcard made out of 2 cards with alsa. I never read any success-stories on that though....

---

