---
title: "Another Feisty-upgrade sound issue"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-04-20
So, I upgraded Feisty through update manager and everything is slightly improved and all that, but my sound is messed up now.  Unlike the other posts I have read where there is no sound, I am only experiencing extremely quite sound.  I don't know if i am being ignorant and this is the same issue, and subsequently i really hate posting an already answered question, but does anyone know what is wrong?  I already checked alsamixer and the levels are all the way up.  I'm running a Sony Vaio FJ series notebook.

---

### Post by Limitlesschannels on 2007-04-21
bump

---

### Post by dangerpl on 2007-04-21
Run this command... 
>  kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto
Unfortunately, it will only work until you restart :/ I didnt figure out a way to make it permanent lol If it doesn't work ask me for a link to a HOWTO on this particular subject. A lot of people are experiencing this problem. And I am only guessing that you have a Toshiba laptop?

---

### Post by bobtherocket on 2007-04-21
I made a fix here....:

[http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound)

---

### Post by Limitlesschannels on 2007-04-21
Actually I have a Sony Vaio, but it seems to be working correctly now... after a quick restart.  Luckily, i won't have to test your suggestion.  Thanks, though, if it happens again, I will keep that in mind.

---

