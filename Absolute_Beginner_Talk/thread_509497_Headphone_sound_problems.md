---
title: "Headphone sound problems"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Nick898 on 2007-07-25
Alright so I've finally gotten into Linux a week ago and everything is working fine! except for the sound that is. For some reason the sound only works when I play music from Ryhtymbox musicplayer, otherwise it is dead silent. 

     Games make no noise, Linux beeps through the motherboard and not through the headphones, and I receive no sound on the internet. Its a USB headphone so I was wondering that this is why, since Alsa seems to work fine with the speakers.

Help would be greatly appreciated! :)

---

### Post by thefoolisme on 2007-07-25
You didn't say, so I have to ask...did you check to make sure that the headphones jack, etc. wasn't muted in the sound board?  If you click on the sound icon at the top right, you'll get a complete board for mics, headphones, etc.

---

### Post by kknd on 2007-07-25
Ubuntu do "motherboard beeps" by default. To disable it, type xset b off.

About the sound:

Try other program that uses alsa (can you hear flash videos lke that on youtube?).

---

### Post by Nick898 on 2007-07-25
Oh wow that was quick! Yeah I unmuted everything and checked it, nada. If I go to file and change device I can see that the headphones are easily detected and that they are on 100% and unmuted.

The headphones also have a small volume control on the wire which changes it. When I press that, the little notifier on screen changes with it.

Oh and no sound on youtube either. By the way, this is the error that comes up when I test it under Preferences-> sound:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.

---

### Post by thefoolisme on 2007-07-25
Another question...you don't have two soundcards installed in your system, right?  Say, one built-into the motherboard, and then a PCI card?  

I only ask because I did when I first installed Ubuntu, and the motherboard sound wasn't turned off in BIOS.  Never an issue with Windows, but Ubuntu used one card for some things, and one card for others.  It was wacked!  :-) 

Or for that matter, if you use on-board sound, is it turned on in BIOS?

Two easy questions, before the techies arrive to swoop you away into terminal land!!  lol

---

### Post by Nick898 on 2007-07-25
Hmm, nope. I only have the on board sound and thats it. Its been annoying me for awhile now so here I am asking hehe. Oh and the rythymbox seems to be not working with it anymore. Says the resource is busy or not available.:confused:

---

### Post by Nick898 on 2007-07-26
Sorry about bumping this but I'm just curious if anyone has an idea of what could be causing the headphone errors. :)

By the way, would pulseaudio and alsa be having a conflict? Just a quick thought on the audio software.

---

### Post by thefoolisme on 2007-07-26
Could you post the info regarding your soundcard, etc.?

---

