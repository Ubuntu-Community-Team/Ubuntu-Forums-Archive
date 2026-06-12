---
title: "Audio playback skips"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by starryeyedboy on 2008-02-23
Hi guys,

Recently (a few hours ago), as I played some songs in Amarok, i noticed that audio playback was skipping. At first, i figured it might be an amarok problem.

Next, when i played songs in Audacious, i noticed the songs were also skipping, in the exact same place.

For example, for song A, it would skip at the same place in the track, each time. When i drag the slider, to force Audacious to play that part of the track, i get this message:

>  Couldn't open audio.

 Please check that:
 1. You have the correct output plugin selected
 2. No other programs is blocking the soundcard
 3. Your soundcard is configured properly 

Playback skips for every single song - just in slightly different places for each song.

I have been using Gutsy for about 3-4 months now, and this has never happened. This kinda started after i installed the Amarok with medibuntu package last night. I'm not sure if that was the cause however.

Could anyone suggest how I might fix this?

Some info:
soundcard: snd_hda_intel
laptop: lenovo 3000 n100
ubuntu version: 7.10 x86_64

---

### Post by jonward690 on 2008-02-23
Hmm have you tried turning up the buffer on your sound card I no that might not be it,it might be worth a try though.Amarok is kinda a resource hog compared to other media players it might be hogging up a lot of resources I am not positive

---

### Post by starryeyedboy on 2008-02-23
Sorry.. how do I do that? I'm really quite new with everything =p

By the way - this skipping doesn't happen only in amarok - the same song skips in the same place, for other players like Audacious as well.

---

### Post by jonward690 on 2008-02-23
Oh ok I am so sorry ,you are new to linux my bad man,sometimes I forget to give better instructions lol anyways I have something that should help you it helped me out when I had some sound issues.Check this link out it is a very good guide to fixing sound problems.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by starryeyedboy on 2008-02-23
Ok, thanks mate =)

I'm gonna go give that a try. cheers!

---

### Post by starryeyedboy on 2008-02-23
Hi again guys,

I've reinstalled my alsa-drivers, and went through the "Comprehensive Sound Solutions Guide"... 

Well, my audio playback is still skipping - does anyone have any idea on what may be the problem? 

I have sound, just that, when playing songs in any music player, the playback keeps skipping...

thanks!

---

### Post by crjackson on 2008-02-23
Strangely enough, I have exactly the same problem on my laptop.  It's not just your audio files either probably.  Try playing back a DVD movie and see if it does the same thing using totem.

The fix for me was installing exile music player.  That fixed music playback problems.  Then I found that the only player for my movies MPlayer Movie Player.  This fixed DVD movie playback.

EVERY OTHER PLAYER (including VLC) give me the skipping problem.  I'm thinking there is a buffer setting somewhere that MIGHT help, but I don't know for sure.  It could also be a chipset issue for Linux.

---

### Post by starryeyedboy on 2008-02-23
I see... alright, i'm going to go install another music player =) and i'll test out some movies right now. 


HM... right now, i've played through several songs with rhythmbox... and it seems to be normal so far. gonna run through a movie now. thanks - its great to know that i didn't have to do some hardcore programming or anything to fix it =)

---

### Post by starryeyedboy on 2008-02-23
Just an update - I've tried rhythmbox and exaile - same problem still happens.

Sound is still skipping during playback Does anyone have any other ideas on fixing this issue?

Note: i have sound, and have tried re-installing alsa drivers, and used several music players.

---

