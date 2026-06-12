---
title: "mac mini dual core audio issues"
date: 2009-02-26
forum: Apple Hardware Users
---

### Post by rock217 on 2009-02-26
I think i've narrowed this down to the analog intel HDA driver, something with the fact that the audio port can do digital *and* analog, but I'm still hoping someone will have a silver bullet for me.

I've checked mixer levels, they're all up.

In sound prefs when I try to switch to HDA Intel stac92xx analog and test I get the following: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

No other options error, but none play back audio.

Apologies if this has been covered already, I've been searching around for a few days in here/google, but alas...

---

### Post by meejah on 2009-03-25
I have a similar problem with Debian "lenny" (latest stable). I can get snd-hda-intel to work with options model=imac24 and freq_position=1. Without the latter there's horrible crackle/static which "mostly" goes away with the latter option. I also tried pulling alsa-driver 1.0.19 from experimental which adds lots more mac-sounding "model" options but none work better than lying and telling it i have an imac24. 

I have not gotten the line-in/mic to work at all with any methods yet.

Any other hints appreciated, especially for the crackling-output problem. It really sounds like interference on the cable or something, but I've tried two different headphones and a speaker system, all of which work fine with an old-gen (powerpc) mac mini.

Cheers,
mike

---

