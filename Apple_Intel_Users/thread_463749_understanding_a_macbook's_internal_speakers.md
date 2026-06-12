---
title: "understanding a macbook's internal speakers"
date: 2007-06-04
forum: Apple Intel Users
---

### Post by vh1 on 2007-06-04
on my macbook (core 2 duo) the sliders in alsamixer have always been a mystery to me

I've been playing around with it for a while now and I think I'm starting to understand it. well, at least expect what certain things will do

master / PCM seem to effect the same speaker. it seems to give out the higher tones. however muting the master channel doesn't do anything at all

so having the master and PCM up all the way results in a lot of treble. every other slider can be at 0. doesn't sound to good

enter the front channel. turning that up makes things *a lot* louder. almost like it boosts the midrange tones. things sound normal now. master does *nothing* with this channel. however bringing PCM back down to zero and there'll be nothing coming out of the speakers

it's like there's 3 different states. to switch between them you can try setting master and front to 100 (or something around there) and put PCM to 50

now, the 3 states I mentioned are: Master: On, Front: On, Master: Off, Front: On, and also Master: On, Front: Off

each produce a different sound. ideally configuration would be set the Master and Front to a safe, identical volume and have the remote / volume keys work with the PCM volume. the only thing with that is that there is no mute control for that channel!

also, there's the pommed options which I haven't considered messing with yet (are the remote and backlight keys this program's main function? the volume keys are working just fine in KDE with the daemon stopped)

if anyone could supply any sort of explanation as to why the speakers act like this it would be great help. because when headphones are plugged in things act normally: mute mutes sound, volume changes volume in a normal way (ie no noticeable differences in tone)

---

### Post by Reb on 2007-06-04
Hi - what you want to do is run gnome-sound-properties, and select only PCM as the controlled track.  Then right click on the mixer-applet and select preferences, set Master and Front to their max values (those channels will stay at that setting, and you will control PCM with your keyboard).  Hope that works!
Edit: should add that that ought to resolve the inconsistent behavior with the internal speakers or headphones.

---

### Post by ivesjd on 2007-06-05
> **Reb said:**
> Hi - what you want to do is run gnome-sound-properties, and select only PCM as the controlled track.  Then right click on the mixer-applet and select preferences, set Master and Front to their max values (those channels will stay at that setting, and you will control PCM with your keyboard).  Hope that works!
Edit: should add that that ought to resolve the inconsistent behavior with the internal speakers or headphones.

That's what I did and it works great.

---

### Post by vh1 on 2007-06-07
> **Reb said:**
> Hi - what you want to do is run gnome-sound-properties, and select only PCM as the controlled track.  Then right click on the mixer-applet and select preferences, set Master and Front to their max values (those channels will stay at that setting, and you will control PCM with your keyboard).  Hope that works!
Edit: should add that that ought to resolve the inconsistent behavior with the internal speakers or headphones.

that seems like it would be the best solution. the only annoyance with that however is that my PCM has no mute control. I'm using KDE, by the way. although alsamixer doesn't have one either so I don't think that could be an issue

---

### Post by vh1 on 2007-06-07
hmm, this setup seems to work perfectly:

set "master" channel (channel to be affected by volume up/down keys and the remote) to PCM in /etc/pommed.conf / kmix
set speakers to Master and headphones to Front in /etc/pommed.conf

now volume keys control the PCM channel, and when the mute button is pressed the Master and Front channels get muted / unmuted

excellent! now I just wish I could do something about kmilo

---

### Post by Gen2ly on 2007-06-07
I probable have to lean vh1 way.  PCM somehow deals with tone.  I set PCM around 88 and use front as my volume contrl.  Seems alright with me
> **vh1 said:**
> also, there's the pommed options which I haven't considered messing with yet (are the remote and backlight keys this program's main function? the volume keys are working just fine in KDE with the daemon stopped))

I think I gotta agree with you.  With Feisty there are now shortcuts for volume control and eject .  It displays (pommedless) on the screen:

If only the function key...

---

### Post by luisbg on 2007-06-26
For the gnome users...

System > Preferences > Sound
The last option in the bottom "Default Mixer Tracks". Just select/double click the PCM track and the function keys will control that.

Right click the volume mixer panel applet go to preferences and also the bottom option handles what that applet controls.

Luis

---

