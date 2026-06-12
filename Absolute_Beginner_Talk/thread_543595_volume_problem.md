---
title: "volume problem"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-09-05
Can anyone solve my low volume problem, which I experience in Edgy and feisty, but not in windows.
Please refer to [http://ubuntuforums.org/showthread.php?t=468553](http://ubuntuforums.org/showthread.php?t=468553)
and
[http://ubuntuforums.org/showthread.php?t=375735](http://ubuntuforums.org/showthread.php?t=375735)
[http://ubuntuforums.org/showthread.php?t=371474](http://ubuntuforums.org/showthread.php?t=371474)

These are not fixed; and I can not get the enhanced sound controls in linux as I get in windows. Can you illuminate?
However, the OS I am now at is Ubuntu feisty 7.04.
And Ubuntu edgy 6.10 has the exactly same problem.

Thanks,
Saurav

---

### Post by gautada on 2007-09-05
Try using the alsamixer directly.  This is accessed via the terminal interface.  

%> alsamixer

I would turn every channel to max one at a time until you discover your volume constraint (probably PCM).  You can do basically the same thing with the gnome-sound-mixer which can be accessed via a right click on the "Volume Control" applet.

---

### Post by sauravbhaumik on 2007-09-05
> **gautada said:**
> Try using the alsamixer directly.  This is accessed via the terminal interface.  

%> alsamixer

I would turn every channel to max one at a time until you discover your volume constraint (probably PCM).  You can do basically the same thing with the gnome-sound-mixer which can be accessed via a right click on the "Volume Control" applet.

That doesn't help; I tried alsamixer from terminal and from anywhere it opened - I reinstalled alsa's latest versions several times. No improvement.
My master volume remains 80%, my PCM remains 80% - it gives the volume which I get in windows with volume 10%.
This is my standard volume - but in windows, I get much devastating volume with master set at 80%.

Why is the difference?
Does anyone notice this difference between windows and linux?

---

### Post by gautada on 2007-09-06
> Why is the difference?

Drivers, The software used to interact with the hardware is different.

> Does anyone notice this difference between windows and linux?

Yes, I experienced the exact same problem.  However, I solved it with what I said previously which was to move everything up to 100% (then leaving alsamixer open) playing sound and adjusting each control down until I found the constraint.  For my sound card I have over 30 controls in alsamixer (you access them with the right arrow).  So for instance if I have master volume at 100% and CD volume at 20% it will only play a music CD at (you guessed it) 20%.  So whenever I have a low volume I go back to the procedure to figure out which control is too low.  The drivers for windows seem to have much less control over the individual outputs by default but I have had the exact same problem in windows in specific instances life CD music.

---

### Post by deadgobby on 2007-09-06
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

