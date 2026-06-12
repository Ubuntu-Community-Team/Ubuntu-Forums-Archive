---
title: "What happened to the Speech?!"
date: 2007-04-18
forum: Assistive Technology &amp; Accessibility
---

### Post by RCC2k7 on 2007-04-18
First it was Microsoft making Narrator less responsible and unusable in Vista and now speech in Gnome 2.18 takes a downgrade too!

Compare the speech quality with Orca in Ubuntu 6.06, 6.10 and 7.04. 6.10 was an upgrade in speech quality when compared to 6.06. Then 7.10 is a downgrade in quality even worse than 6.06. That eSpeech engine reminds me of the ultra-robotic synthesizer cards that you used to stick in Apple IIe computers in the mid 80's.

What happened to festival/festvox?

---

### Post by Henrik on 2007-04-20
> **RCC2k7 said:**
> What happened to festival/festvox?

We switched to a speech engine called eSpeak for several reasons: 
[LIST]
[*]it supports many more languages (which is important for those who don't speak English)
[*]it's more lightweight and resposive, which many prefer
[*]it performs better at high speech rates
[*]it takes less space on the CD so we now have place for the additional languages by default[/LIST]Festival is still available in the main repositories. Just use the Synaptic package manager to install it.

---

### Post by RCC2k7 on 2007-04-20
Those are good reasons. Thanks for the reply.

Ironically, US English doesn't seem to be supported by eSpeak; all the English voices seem to have UK accent. I'll look for Festival in Synaptic.

---

