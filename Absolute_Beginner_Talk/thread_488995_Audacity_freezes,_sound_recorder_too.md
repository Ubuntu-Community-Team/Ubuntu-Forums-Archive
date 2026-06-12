---
title: "Audacity freezes, sound recorder too"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by AuroraManson on 2007-06-30
I cannot seem to get either of them working or find any other sound recorder beyond them.

Every time I try to record it just freezes! How do you force quit a program if it doesn't pop up an option?

Help.. =( I need to use audio record.

---

### Post by expatCM on 2007-06-30
How did you install Audacity?

If you want to stop a frozen program you can either use the command line or go to System / Administration / System Monitor / Processes and there scroll down the list, highlight the item and stop it ...

---

### Post by AuroraManson on 2007-07-01
i installed it via applications > add remove 

It still just freezes I can't record :(

is there any other reliable program out there?

---

### Post by expatCM on 2007-07-01
Trouble is that Audacity is more or less "the" standard.  It is reliable, stable and works.  So if it is not working for you it is not impossible to suggest that other programs may also have problems.

In resolving the issue my personal inclination would be to uninstall Audacity and then go to Synaptic and install again.  The reason for using Synaptic is to see if there are any dependencies also being installed.  If that did not resolve the issue then my thinking would be a little broader in that I would think that Audacity was working fine and that the problem was related to say your sound card.

Indeed thinking about the sound card may be a good foundation.  Do you have a sound card integrated with your motherboard and do you have a separate sound card installed?   If you do, are you sure that Audacity is using the right device?

If you want to test your recording function there is a program called Sound Recorder which I think is standard and found under Sound and Video.  You should be able to record from here in order to test .....

---

### Post by AuroraManson on 2007-07-01
I reinstalled it through synaptic.

I don't know which one my audio is but none of the settings would record but only when its set to OSS:/dev/dsp

do I need to install my drivers?

---

### Post by expatCM on 2007-07-02
Open the command line and type

alsamixer

look at the top left of the window which will open and it will tell you the name of your sound card.  What is it?

---

### Post by AuroraManson on 2007-07-02
Card: HDA Intel
Chip: SigmaTel STAC9250
View: [Playback] Catire A;;
Item: Master [dB gain=0.00, 0.00]

---

### Post by expatCM on 2007-07-02
This thread appears to be not unrelated to what you are experiencing
[http://ubuntuforums.org/showthread.php?t=360867](http://ubuntuforums.org/showthread.php?t=360867)
would you please have a look through and see if you see any similarity

The solution in that case was suggested to use a different sound card.

---

### Post by AuroraManson on 2007-07-08
it won't play audio either...

I tried every single device I select doesn't work

and all it says it "error while opening sound device.  Please check the output device settings and project sample rate"

---

