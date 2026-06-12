---
title: "front panel buttons on laptop - audio config question"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by emarkd on 2007-05-22
Thank you for taking the time to read this post.  I'm a pretty fast learner but this one has got me stumped so far...

I've been running edgy on my dell inspiron 6000 laptop for about 6 months or so and I love it.  I've been slowly configuring it to work just like I want it to, which is great because Windows would never let me do that.  Anyway, to the issue at hand...  I've got an Audigy2 PCMCIA audio card in the laptop along with the onboard intel audio chip.  Both work fine - one at a time.  I've written a short bash script that reconfigures alsa depending on which card I want to use at the moment, since the audigy card sounds so much better through headphones, but can't playback through the built-in speakers.  My problem is with the volume buttons on the laptop case.  They always control the master volume for the intel card, even if the audigy card is currently being used for playback.  The little volume applet in the gnome panel at least has a dialog box device selector, where I can change what it controls.  How do I do this for the buttons in the case, preferably from the commandline so I can integrate it with my existing script?

---

### Post by steevols on 2007-05-22
Well, what I would do theoretically would be this.

Head to a terminal and track down the bin for that applet (probably gnome-audio-control or something like that), and run it with the --help extension. Or, read its man-page, if it has one. Hopefully, that will yield a command to change your master.

---

### Post by emarkd on 2007-05-23
thanks for the reply, but i think i was unclear.  i don't want to change the audio settings for the panel applet.  i want to change the settings for the keyboard media buttons.  i don't know what software controls those buttons in ubuntu, other than the keyboard shortcuts option on the preferences menu, and with that applet, all i see are options for volume up and volume down but these still only seem to affect the one audio card.  i want to edit the media buttons so they affect the other sound card instead of the onboard audio.

---

