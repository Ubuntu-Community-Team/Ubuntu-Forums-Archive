---
title: "microphone (or sound card...) not working"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-10-06
Hello guys!

I installed ubuntu on a friends PC and it looks like some things just don't work, as easily as on my machine:)

Like the microphone.
I red other posts, but nothing looks like this problem.

In alsamixer I can't find any comlums for capture.
When I run vumeter -r & I get the following error message: Cannot connect to sound daemon. Please run esd at a command prompt.
Then:
@The-Machine:~$ esd
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.

In the sound preferences at sound capture I can put anything, this is the error message that I get:
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not establish connection to sound server

An another thing: when amarok (or other music playing things) is playing no other sound works.
Example, amarok is playing, trying to play something with audacious, the error message is: 

Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.


So, if anyone has some ideas, what to try, I will gladly do it:)

Thanx!

---

### Post by duruttye on 2007-10-06
Another thing: in alsamixergui there are two red dots above the mic...

Is there something similar to reconfigure the sound card, like reconfigure the xserver-xorg???

Anyone?
Any suggestions?

thanx

---

### Post by ronocdh on 2007-10-06
Sound performance (as with many other things yet in Linux) is *highly* dependent on hardware. This means that certain soundcards, for instance, are more well supported than others. It's entirely possible that your soundcard just isn't well understood by Ubuntu, because the manufacturer of it has not disclosed its specifications well enough to allow free drivers to be written for it.

But before we get so dire, I would fool around for a long time in the sound preference panels, trying different available output devices and testing. Of course, you can always [check the ALSA page]("http://www.alsa-project.org/main/index.php/Matrix:Main") to see whether your card is listed as supported.

---

### Post by duruttye on 2007-10-06
I checked out that page, but the probelm is that, as I said before, it is my friends pc, and we dont know what kind of soundcard it has. This is the first problem...
At first there were two sound cards, but in sound preferences, I figured it out, that the it didn't know wich one to use, so we removed one of them. Is it possible, that after the removal, for sound capture, ubuntu still wants to use the other sound card? That's why I asked, if it is possible to reconfigure something, so it will know, that there is only one sound card???

Thanx for the answer:)

---

### Post by duruttye on 2007-10-06
Look at this:

@The-Machine:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I searched the forum, and it looks like we are not the only ones that have problems with this sound card and microphone use.

So, if anyone had the same problem, and somehow figured it out, please let me now, and the others having the same problem.

thanx guys

---

### Post by cherry316316 on 2007-10-08
> **duruttye said:**
> Look at this:

@The-Machine:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I searched the forum, and it looks like we are not the only ones that have problems with this sound card and microphone use.

So, if anyone had the same problem, and somehow figured it out, please let me now, and the others having the same problem.

thanx guys

[http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

---

