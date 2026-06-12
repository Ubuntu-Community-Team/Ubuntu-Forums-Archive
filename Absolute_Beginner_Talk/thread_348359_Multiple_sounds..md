---
title: "Multiple sounds."
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by MC_Jonn on 2007-01-28
Hey, this is my first post here. I am a newbie, just shifted from XP, on the way also tried FC6, most of the hardware wasn't recognized esp. wireless, but with Ubuntu 6.10, everything worked out of the box, amazing! 
         I don't know if this has been discussed before. My problem is that i seem to get multiple audio channels while using my laptop. Its like even though i have plugged in my headphone's i still hear music coming from my laptop speakers, I haven't done anything from my side to configure the audio card, it worked right from the start .
         Happens even when i plug in my stereo, its supposed to stop right? If this has been discussed before can anyone post a link, thanks a lot anyway. I have got the on board Intel sound.

---

### Post by ComplexNumber on 2007-01-28
i haven't really got much to go on, but it may be because the correct sound drivers aren't being used. install alsamixer. then in asamixer, go to File, then Properties.

---

### Post by 13east on 2007-01-28
i'm getting the same problem for my pavillion zv5000z laptop.  i can get the headphone to work but the built-in speakers stay on; i have to manually go into the alsamixer to turn off the master volume but still cannot control the headphone volume through the buttons on the laptop.  is there anyway to setup my system to automatically turn-off the master volume when the headphones are plugged in and control the volume level through the laptop's external buttons?

---

### Post by samden on 2007-01-29
Same problem here with an iMac G3.

You can try using alsamixer (type "alsamixer" into a terminal window). This may fix the problem. Two little hints - for a list of the commands to use when in alsamixer, press "h". To turn a function on or off press "m" for mute.

I have found that on my computer headphone detection is turned off. I can turn this on through alsamixer, but when I close alsamixer and open it again, headphone detection is again off. I have no idea what to do about this - if anyone has any suggestions I would be very grateful.

---

