---
title: "I can only play sound with one application."
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by linuxcity on 2006-04-29
I'm wondering if there is a way to allow multiple applications to share the sound card. If I were to play music with one application, I cannot do anything else that needs sound. For example, I cannot do voice chat (skype) while I'm playing the music or play music in another application. I noticed that MS Windows allows sound to play in multiple application all at once. Thanks all for the help.:confused:

---

### Post by Kethinov on 2006-04-29
What sound card?

If you could do sound mixing in Windows, then it's likely either A. ALSA's mixer doesn't support your card or B. Ubuntu screwed up the setup of your soundcard.

Either way, you need to tell us what soundcard you have before we can help you. And in order to get it working, you need to find out if Linux supports hardware mixing on your card. If not, you can look into doing software mixing. Sadly, I don't know much about setting up this stuff, as I've always used soundcards with good Linux support. Every distro I've ever used setup my soundcard for me perfectly. But good luck.

---

### Post by linuxcity on 2006-04-30
I'm running latest Dapper on the Thinkpad T40. This is the sound card specification from IBM.
Analog Devices AD1981A AC'97 SoundMAX Codec (Full-duplex)

---

### Post by gezzabob on 2006-04-30
Yes I have notice the same problem when only able to have one app using sound :confused: ...

lspci returns among ohter things the following....

0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

Its a gigabyte ga-7nnxp mobo with on board sound I beleive AC97 audio.  Running breasy 5.10.

any ideas how I can get my sound set up properly,  I didnt think much of it until I read this post.

Sorry to jump on the band wagon so to speak. 

PS the sound card is capible of multiple apps using at the same time it did in windows.

---

### Post by zaccc on 2006-08-03
sound seems to work fine on my setup, i can have sound using an audio app and  gaim for example, however, no sound with Listen and Firefox, i have to shut down Listen for youtube or w/e to work

---

