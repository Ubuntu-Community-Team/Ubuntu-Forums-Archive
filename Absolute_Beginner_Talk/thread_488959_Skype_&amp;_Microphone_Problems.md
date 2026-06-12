---
title: "Skype &amp; Microphone Problems"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by danmpem on 2007-06-30
I am a newbie, but from what I can tell, there are a lot of problems with Skype and microphones on Linux.  Here is my setup and what I have tried:

Ubuntu Feisty Fawn
Skype 1.04
KDE Desktop

My normal microphone functions are all working as far as I can tell.

My mic volume settings are all turned up as well as capture levels.

I tried the alsamixer -V capture -c 0 command on the terminal and turned everything else up.

But the Skype test call still is telling me that my microphone isn't working.  What should I do?

Thank you

---

### Post by farueulogy on 2007-06-30
In skype click the *cog icon* at the bottom for the main menu, select *options*, select *sound devices* from the left panel and select your specific sound device from the lists rather than "default sound device".

If that doesn't work have a fiddle with all the sound devices available.

Otherwise I'm stuck. Can you record your microphone from a program like audacity?

---

### Post by ub_one on 2007-06-30
Hi,

I have the same trouble my mic. I don't know how to detect the problem....Sound Recorder or Audacity CAN NOT record any sound. One thing is that my mic is integrated (don't know how helpful that is...).
Appreciate any advice....

---

### Post by danmpem on 2007-07-15
AH!  I got it!  I got it!  Okay, the solution for me was in a really obvious/simple place, but the solution itself was not simple.  I found this site here ==> [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html) and it made a really good point of checking the green and red LED's on KMix, so I checked it out.  I did some playing around with the settings on my mic, capture, and recording, and then I got it.  Below are my KMix options.

Oh yeah, and I also have two sound cards - one integrated and one in a PCI slot.  And since I don't want to use the integrated sound, I disabled it through the BIOS.  Ubuntu software has a much easier time dealing with my sound card (some of the software would work with the integrated and some with the PCI card).

---

