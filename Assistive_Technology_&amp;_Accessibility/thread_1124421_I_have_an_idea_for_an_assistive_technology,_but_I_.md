---
title: "I have an idea for an assistive technology, but I need to find a Voice Recognition..."
date: 2009-04-13
forum: Assistive Technology &amp; Accessibility
---

### Post by ChocoTuar on 2009-04-13
...API. I've looked at many different (incomplete) speech recognition platforms, but they all either require me to build my own acoustic model from the ground up (with hours of acoustic test data for it to parse) or they simply won't compile on my system.

My idea is to make an AIM client that captures your voice, sends that as an IM, and takes the received IM's and pipes them through espeak so it's an audible response. The key difference from VoIP is that only the user afflicted requires the special client, and the user on the other end might not even know. You could even pump it full of voice-activated controls and such, but right now I'm simply stuck at finding a working voice recognition API.

I've tried so far:
julius
sphinx (requires me to build it from the ground up)
ISIP (this one seemed promising, but wouldn't install)
cvoicecontrol
XVoice

Any idea on where I could start? Just something that includes the acoustic and dictionary models by default, even if they kinda suck. I want to at least see if it'll work before I push a ton of hours into this.

---

### Post by linuxuser21 on 2009-04-13
Have you tried [Festival]("https://help.ubuntu.com/community/TextToSpeech")?

---

### Post by glotz on 2009-04-13
Try here [http://voxforge.org/](http://voxforge.org/)

---

### Post by ChocoTuar on 2009-04-13
Festival is text-to-speech. I'm looking for speech-to-text.

---

