---
title: "Audacity/Soundcard Issue"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by adarkmethod on 2007-03-05
Alright, my sound has been working fine, as a matter of fact, I've got Darkest Hour cranking out of this machine right this second. But when i open Audacity, it says i Have no input or output device, and it wont open te lsit for me to select them.

What do you need to know, and how can i get that info for you using Ubuntu 6.10.

Thank you in advance, you guys are all great

---

### Post by adarkmethod on 2007-03-05
i tried the kill ESP trick, but i still got Audio I/o error "you will not be able to play or record files"

---

### Post by adarkmethod on 2007-03-05
anyone had a similar problem or know a fix?

---

### Post by ignignokt00 on 2007-03-05
I need similar help.  I've got something plugged into the line-in on my SB Audigy 2 card, and I'm getting nothing (it's all turned up in ALSA mixer).  In audacity I/O prefs, the sound I/O are both set to /dev/dsp with no other options.  Please, help.

---

### Post by ignignokt00 on 2007-03-05
small update:  Using "Sound Recorder," I can get line-in audio by selecting "analog mix" as the input.  I'd just really like to know how to get the full input options in audacity.

---

### Post by konungursvia on 2007-03-05
Me too, i can use audacity but i have to listen to the audios on movie players. :(

---

### Post by adarkmethod on 2007-03-05
i still jsut get Audio I/o error "you will not be able to play or record files" despite my card working fine for other programs

---

### Post by adarkmethod on 2007-03-12
ok, installed Ubuntu on my desktop, full Ubuntu, no dual Boot, Edgy 6.10. Its using an Intel 82801AA AC'97 Audio old POS soundcard, I can play my guitar through the computer and it comes out fine, but when i turn on Audacity it delays about 1.5 seconds and sound like mushed crap.

please please help me, i really need this program or something similar if Ubuntu is going to be a permanent solution for me

---

### Post by xcat442 on 2007-03-13
Hello,

It sounds like the program you are listening to music with has locked the ALSA program or the I/O port to the sound card and will not let other programs use the port at the same time. I had this simular problem with Audacity and could only use it if it was the only multimedia program open.

Try Streamtuner. Can be installed using applications Add/Remove May be it will be a good match. Not totally sure how to fix the above problem, but this seemed to be a good solution at the time.

[http://www.nongnu.org/streamtuner/](http://www.nongnu.org/streamtuner/)

Peace

---

### Post by adarkmethod on 2007-03-13
than, i'll check it out

---

### Post by djen9999 on 2007-03-13
I get the Audio I/o error "you will not be able to play or record files" error in Audacity only  if I previously used another program that needs the sound card.  There must be some pointers that aren't being reset.  If I restart the computer, all is well.  It's a pain but it's the only solution I've come up with.

---

