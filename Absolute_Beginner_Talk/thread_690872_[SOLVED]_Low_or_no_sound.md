---
title: "[SOLVED] Low or no sound"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-07
Okay, I'm back with what I am sure is a very stupid question!

I finally bought the cheapest speakers that Wal-Mart sells ($10 - hook up to the speaker jack on the sound card and to a USB port).  I previously just plain didn't have any speakers on this old PC, but I needed something to hear sound with as I try to edit some basic video.

Well, I've got 3 devices listed in Volume Control:

(1) Aureal Vortex au8820 (Alsa mixer).  I have tried external amplifier being checked and unchecked with no difference.  I have Line-in, Microphone and Phone all muted, the rest (Master, PCM, CD and PC Speaker) are set to maximum volume.

(2) VOIP USB Phone (Alsa mixer).  It only has 1 control for playback (PCM) and it is set to the maximum.

(3) SigmaTel STAC9704 (OSS Mixer).  It is just like (2) above.

When I go to System/Preferences/Sound and try the "Test" button on Sound events, Music and Movies and Sound playback on Audio Conferencing I get an extremely faint tone in the speakers.

If I go to the Sounds tab and try something "Play" on the login sound I hear nothing.

I hear no other sound anywhere else.

When booting and shutting down you can here some of the system noise (I'm sure it's about the cheapest sound card available!).

So, while I can answer some simple questions for some people, I'm back asking for help on another simple thing myself!

Any help would be appreciated!

Thanks!
Dave
:)

EDIT:  I should add that changing from autodetect and any of the other sound devices seems to make no difference - just the tone on those that do work.

---

### Post by anewguy on 2008-02-07
BTW - the sound card appears to be a Vortex 1.  I've seen mention on the net about adding the module via /etc/modules, but they were for other sound cards or chipsets.  Does anyone know if there is a Vortex 1 module I can add somehow to /etc/modules so the kernel knows about the card?

:)

---

### Post by anewguy on 2008-02-07
I am officially a dumb-*** !!!!  Of all the STUPID things - just found out these speakers have a VOLUME CONTROL ON THE SIDE!!

What a flippin' idiot I am!:):)

---

