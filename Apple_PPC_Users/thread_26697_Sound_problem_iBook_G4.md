---
title: "Sound problem iBook G4"
date: 2005-04-13
forum: Apple PPC Users
---

### Post by fiskio on 2005-04-13
Hi,

i'm having this weird problem with sound on hoary: it is VERY low and i can't turn it up.
I mean i can but it gets very distorted and it's still low.
There is also what i called "The Pillow Effect", the first half of seconf of a sound is nice and loud, but then it fades immediatly like somebody put a pillow on the speakers.
I am using the standard powerpc kernel from hoary, i tried 2.6.11 and 2.6.10 but i got the same problem. I was having it with debian too, using kernel packages higher than 2.6.7 (in the 2.6.7 everything was fine).
I tried disabling esd, using OSS and ALSA....

right now i am using OSS and listening to the music at a VERY low volume :(
snd_powermac          48292  1
snd_pcm_oss            67552  1
snd_mixer_oss          23136  1 snd_pcm_oss
snd_pcm                   111492  2 snd_powermac,snd_pcm_oss
snd_timer                 29540  1 snd_pcm
snd                          68020 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore                11940  2 snd
snd_page_alloc         11716  1 snd_pcm

thanx

MF:

---

### Post by ssam on 2005-04-13
it may be one of the hidden volume controls

right click (f12) on the volume control and chose 'open volume control'
then go to edit -> preferences in the volume control,  tick on all the 'tracks' and click close.

now play with the sliders. the DRC one seems to make the difference for me (on a titanium powerbook G4).

hope that helps

sam

---

### Post by chascon on 2005-04-14
I did an upgrade from sarge to hoary and I did not have sound wither on my ibook G4 2004 yr model.  I noticed that verbose boot said something about "alsa not configured? Run alsactl?.  When I mentioned this to my firend he took care of it before I cold take notice of hwhat he had exactly done.  I had sound after that.  Point of the story is if  have sound on my G4 you should have it as well, or the ability.  Read the verbose output, take note of what it is asking you to do, google that, and fix.

---

