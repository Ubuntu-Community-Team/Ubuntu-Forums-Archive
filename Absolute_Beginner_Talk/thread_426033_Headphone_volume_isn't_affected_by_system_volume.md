---
title: "Headphone volume isn't affected by system volume?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by The AlGorenator on 2007-04-28
As the title so clearly states, i have found that if i use my headphones, no matter what setting the volume is on, the headphones function as if it is set to the maximum. 

Is this a bug? Is there a fix for this?... or is my particular install/harware just dodgy

Using fiesty, btw.

---

### Post by Martin on 2007-04-28
Dumb question: is it plugged into line out socket or the headphone socket?

---

### Post by The AlGorenator on 2007-04-28
The headphone socket.

---

### Post by Martin on 2007-04-28
What are you using to try and adjust the volume? Does your pc have dedicated vol keys, is it a laptop with soft buttons or are you using the volume slider on the panel? If you double click on the panel volume slider - what do you see? Also once you've done that and the more detailed vol control is open - take a look atthe option under 'Edit' 
I am asuming at this point that sound works generally though, just thatyour headphone vol seems to be acting up?

---

### Post by steve.horsley on 2007-04-28
There are two different sets of preferences you can tinker with. Firstly, double-clicking the panel speaker icon gets you a bank of sliders to play with, and the Edit->Preferences menu there makes other sliders appear and disappear. Secondly, right-clicking the panel speaker icon and choosing Preferences gets a dialog where you can choose which of the sliders the panel icon slider will adjust.

---

### Post by The AlGorenator on 2007-04-28
OK. When i use teh buttons on my pc, or the master volume, it doesn't correlate with the headphone volume. Any way i can get the two to sync, or no?

---

### Post by vanadium on 2007-04-28
Additionally, what application are you using to generate the sound? I use the media player XMMS, and it has it&#347; own volume control: it does not respond to the settings from the desktop bar speaker icon. In Linux, different systems coexist to generate sound, and different apps might use different systems.

---

### Post by Jeff Gavett on 2007-05-02
I'm on a Dell Inspiron 6000, having a similar issue with all programs through headphones. I can adjust it manually through the alsa mixer, but my buttons always adjust the master with no effect on the headphones.

---

### Post by teasum on 2007-05-05
Just my two cents: I have added Volume Applet to my gnome-panel twice, and I have one set to the master volume, and the other for my headphones.  My media buttons on my Inspiron 8600 only control the master volume, i.e. the laptop speakers.  I like this arrangement, actually, because I can make sure the speakers are off and the headphones on--this means when I start up my laptop in the library, it won't make a loud startup sound, but if my headphones or extra speakers are plugged in, it will.  

I agree, however, that there should be a way to choose which set of speakers--main or headphone--the volume buttons control.

---

### Post by drFUNK on 2007-05-09
> **The AlGorenator said:**
> As the title so clearly states, i have found that if i use my headphones, no matter what setting the volume is on, the headphones function as if it is set to the maximum. 

Is this a bug? Is there a fix for this?... or is my particular install/harware just dodgy

Using fiesty, btw.

For feisty, go to System>Preferences>Sound, hold the control button and click master and headphone under "Default Mixer Tracks."  These should make your volume keys control the volume for both sliders at once - at least this works on my friend's Inspiron 9300.

---

### Post by jkblacker on 2007-05-13
Thanks drFUNK, this helped me on my own Inspiron 6000 - it's great what a little forum-searching will do for a problem.

---

### Post by drFUNK on 2007-05-14
> **jkblacker said:**
> Thanks drFUNK, this helped me on my own Inspiron 6000 - it's great what a little forum-searching will do for a problem.

No problem, I'm glad i could help!:)

---

### Post by xflbret on 2007-05-25
helped me too. thanks

---

