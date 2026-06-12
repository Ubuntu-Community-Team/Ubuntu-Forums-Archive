---
title: "Newb: Not getting sound from audio input jack."
date: 2011-09-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by noahdiehl on 2011-09-06
Hi everyone,

Total newb here (just installed Ubuntu yesterday) but have been able to troubleshoot a few issues by scouring the forums but I got one I am not finding anything on (sorry in advance if I missed a post similar to this that has been resolved).

I have installed Ubuntu 11.04 Unity on an HP Pavilion a6109n Desktop PC (specs say the mother board is a "Asus M2N68-LA"). I am using the on board audio (front and rear jacks are giving me the same issue) and I am not able to pump sound to my speakers from the audio input jacks. I have sound... just nothing from the input jacks.

I opened the "Sound Preferences" and under "Input" I am able to to select "Audio Line-In" in the "Connector" spot... and when I connect my iPhone and push play I notice that the "Input level" indicator bounces around as if it's getting something... but I get nothing out of my speakers. :confused:

Well, being a new to Ubuntu I am sure I am missing something simple... might anyone be able to help?... to please who ever made these emoticons there is a bucket of popcorn in it for ya.

 :popcorn:


Thanks for any help you guys can give,
Noah the newb

---

### Post by Daniel_JS87 on 2011-09-06
Open a terminal (ctl+alt+T) and type alsamixer. Check the levels for Master, Front, and Line.

---

### Post by noahdiehl on 2011-09-06
Oh, nice... CTRL+ALT+T was new to me, lol.

I found that "Line" and "Line 1" were at 0, turned them up all the way and exited... but still nothin'.

---

### Post by noahdiehl on 2011-09-06
If it helps at all "Card: HDA NVidia/Chip: Realtek ALC1200".

---

### Post by Daniel_JS87 on 2011-09-06
Try this[ http://ubuntuforums.org/showthread.php?p=7279149#post7279149.]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

---

### Post by noahdiehl on 2011-09-07
No dice :/

I have audio, but I can can't seem to use the input jack.

I did...

     Code:
     sudo gedit /etc/modprobe.d/hda_intel.conf 

and paste this in it.

     Code:
     options snd-hda-intel model=auto probe_mask=1 


...did not help the problem but now I notice if I try to "Test Speakers" under "Hardware" in the "Sound Preferences" don't any sound from the test... so un-did what I just did, lol.

Thanks for trying to help me.

---

### Post by noahdiehl on 2011-09-10
Bump

---

### Post by as2000 on 2011-09-13
Install gamix. I had the same issue with my desktop and once I installed it, I played around with the controls and turned off Independent HP and it worked.

---

### Post by JooseyJay on 2011-09-13
Had the same problem with my sound, I don't remember everything I did but one of them was:

```
options snd-hda-intel model=basic
```Also I did pretty much step 1-6 from this page...

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by noahdiehl on 2011-09-26
Installing gamix did the trick... also known as ALSA Mixer in the Software Center.

Thanks sooooo much dude!

:popcorn:

---

