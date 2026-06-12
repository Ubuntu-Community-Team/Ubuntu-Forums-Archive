---
title: "[SOLVED] help with getting 5.1 sound with a new soundcard"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by satanic-yobbo on 2008-03-26
i have just installed a new soundcard which is a dell soundblaster live from creative and i can get some sound but i cannot get the 5.1 true surround happening.. can someone give me any ideas on how to get tru surround ( or indeed even surround at all) to work with this card 

 and please dumb it down a touch for me if possible as i am still pretty much a noob to linux and still learning a lot and also want to avoid like the plague having to do a fresh install if i can get out of if at any cost

---

### Post by northern lights on 2008-03-26
From a terminal run ```
alsamixer
``` Is "Surround" muted, maybe? Or turned all the way down?

MM - muted
OO - not muted

---

### Post by satanic-yobbo on 2008-03-26
no all is fine there & i can run in teminal a sound test and have it all come through fine eg: front left..front right ..etc just when watching movies or music it comes through in stereo sound

---

### Post by northern lights on 2008-03-26
Then it's up to the software. What player do you use? Whichever it is, you'll have to fool around with Audio Output settings.

Post the player and I'll give u more detailed steps...

---

### Post by satanic-yobbo on 2008-03-26
i use amarok or rhythmbox but i am always open to suggestions on any new software that might be a little better or have some other cool features lol

---

### Post by kpkeerthi on 2008-03-26
> **satanic-yobbo said:**
> no all is fine there & i can run in teminal a sound test and have it all come through fine eg: front left..front right ..etc just when watching movies or music it comes through in stereo sound

Music are stereo in most cases unless you are listening to one that has 5 or more channels encoded in it (something like [this]("http://en.wikipedia.org/wiki/5.1_Music_Disc"))

As for the video, are you watching a 5.1 DVD movie or ripped ones (like an .avi file) ?

---

### Post by satanic-yobbo on 2008-03-26
lol ok yeah  i just realised that the movies are .avi ripped onesand thus do not likeley have 5.1 sound on them   hahaha i know im a dumbass but thanks to a separate problem with my dvd player telling me that i havent got licence or permissions or something to play specific dvds i cant test wether the 5.1 dvds actually give me tru sound

---

### Post by kpkeerthi on 2008-03-26
LOL! OK.

I have a similar Creative Audigy 2 ZS soundcard as yours. I use VLC player for watching DVDs. 5.1 does work for me. I'm sure it will work you too.

---

### Post by satanic-yobbo on 2008-03-26
yes i think so too i just have to get the permissions error fixed so i can sit back and enjoy pink floyd the way it was meant to sound now lol cheers for the help :)

---

