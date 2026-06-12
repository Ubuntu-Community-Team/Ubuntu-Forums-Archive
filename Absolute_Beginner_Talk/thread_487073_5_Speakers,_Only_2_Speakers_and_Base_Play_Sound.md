---
title: "5 Speakers, Only 2 Speakers and Base Play Sound"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by samasaur on 2007-06-28
I managed to fix the squeaky sounds I had from before. But I was wondering if anyone knows how to enable surround sound on ubuntu. At the moment only the two front speakers have sound playing out of them. The two rear ones are completely silent. The base seems to work fine too. So if anyone can help out thanks in advance.

---

### Post by limbourg31 on 2007-06-28
did you check out the system-prefs-sound and configure your speaker? this link might help [http://www.linuxforums.org/forum/ubuntu-help/94148-surround-sound-ubuntu.html](http://www.linuxforums.org/forum/ubuntu-help/94148-surround-sound-ubuntu.html)

---

### Post by kpkeerthi on 2007-06-28
Open terminal and type alsamixer. Play with the controls and see if it helps.

---

### Post by samasaur on 2007-06-28
Yes I tried alsamixer in terminal but it didn't work. Only managed to change the sound of the front speakers. The rear speaker controls had no effect on the speakers at all.

---

### Post by kpkeerthi on 2007-06-28
btw... what sound card do you have? Also... did the surround sound ever worked in windows or previous versions of ubuntu?
I hope you would have already tried this... do you have all your green, orange and black cables connected to the correspoding jacks of your sound card?

---

### Post by samasaur on 2007-06-28
I have a Creative Sound Blaster Live 5.1. It did work well with XP and I have checked the cables, nothings wrong with them.

---

### Post by kpkeerthi on 2007-06-28
Lets try one last thing... 

1. Backup .asoundrc in your home folder.
```

mv .asoundrc .asoundrc.backup

```

2. Reboot and check if speakers work. If not, use alsamixer and adjust the sliders and see if it helps.

---

### Post by kpkeerthi on 2007-06-28
You may also try [ this tip]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA")

---

### Post by Pzkpfw on 2007-07-08
If my speakers don't play 5.1 surround while playing a dvd, does this mean that my sound card is borked?

---

### Post by daulex on 2007-10-30
> **Pzkpfw said:**
> If my speakers don't play 5.1 surround while playing a dvd, does this mean that my sound card is borked?

good question, if the dvd does have 5.1 encoded on it, then in theory every speaker should be used, if that does not happen and your asoundrc file is ok, I would guess that yes it may be broken

---

