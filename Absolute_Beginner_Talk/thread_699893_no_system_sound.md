---
title: "no system sound"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by flowevd on 2008-02-17
hi,

I followed the sound faq but couldn't see a remedy for this problem.

I hear the startup sound perfectly and sound from media playback, but i never hear a peep out of most of the system sounds. all the 'test's in the sound dialogue box give me an audible tone and all of the sounds are assigned in the neighbouring tab. What's going on? I'm running 7.10 on a dell m1330 xps laptop.

thanks for any help

---

### Post by ravosava on 2008-02-17
Dunno if this will work for you but:

Try restarting alsamixer...

I had a similar issue and a friend told me to just restart it...

Open up a terminal and type:

killall alsamixer

---

### Post by Crafty Kisses on 2008-02-17
> **flowevd said:**
> hi,

I followed the sound faq but couldn't see a remedy for this problem.

I hear the startup sound perfectly and sound from media playback, but i never hear a peep out of most of the system sounds. all the 'test's in the sound dialogue box give me an audible tone and all of the sounds are assigned in the neighbouring tab. What's going on? I'm running 7.10 on a dell m1330 xps laptop.

thanks for any help

Try to see if all your volume controls are turned up, or take a look at alsamixer.

---

### Post by flowevd on 2008-02-18
thanks for your help.

all volumes are at max. have tried muting those which don't make a difference, to no avail.

i don't know if this is relevant, but when I try to set the 'sound events' device to 'ESD' - the option i have to select if i don't want all system sounds greyed out on the 'sounds' page - i get the following error message.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

does that mean anything...?

---

