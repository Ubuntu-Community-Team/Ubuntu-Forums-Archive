---
title: "what did I do to my sound"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by hwttdz on 2006-10-04
After installing ubuntu I looked for a way to play music files, esp mp3, after having some initial trouble with different apps I decided to install a few more apps using synaptic.  Before I touched anything I was able to get sound from XMMS, though I do not know the settings, now not only can I not get sound from XMMS I cannot get sound from anything (including the soundcard check in the devices manager).  I think I would like to use banshee, namely something similar to itunes as that's what I'm familiar with.  I'm not even quite sure how to determine what sound card I have, or if linux needs drivers, how I'd get those, I might even have something muted, though I don't think so (the disadvantage of having volume controls in 10 different places).  I pretty much have no idea.  Thanks for any help.

I think it may be significant that I also have no sound on cd.  Sound Juicer progresses through tracks but still no audio.  It's not the speakers as I have sound in windows.

---

### Post by Kateikyoushi on 2006-10-04
Follow [this guide]("http://http://ubuntuforums.org/showthread.php?t=205449") it is a great help in sorting out what went wrong.
The more information you collect the easier we can help.

---

### Post by hwttdz on 2006-10-04
Note the guide referenced can be found at [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by hwttdz on 2006-10-04
My soundcard is showing up using 
$aplay -l
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
and on alsamixer I unmuted a few fields (surround, mono) that shouldn't matter anyhow.  Saved those settings but still no sound.

---

