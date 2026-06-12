---
title: "Curious sound problem"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by ComplexNumber on 2007-01-12
i can play audio cd's/dvd's and mp3/ogg files using applications such as Listen and Exaile perfectly fine. the startup/shutdown sound works too. 
HOWEVER,  i cannot get any sound in the following:
-YouTube videos
-audio applications such as gtick, solfege, hydrogen, denemo, etc.

i've noticed that the ONLY way to activate these sounds is to start up the following applications(the applications shown in the screenshot) in the menu and press the 'Test' button. when i do this, the sound from the above applications(and YouTube) doesn't start right away. instead, if i reboot my computer, the next time i log in, the sound in the above applications works:
-main menu -> system -> preferences -> sound
-main menu -> system -> preferences -> multimedia systems selector



does anyone know why this is so? it seems as if pressing the Test button seems to bring the sound server to life, but why it only works the next time i reboot and log in is a mystery. i've gone through all the manuals on this forum and elsewhere, but they don't seem to solve it or point to the actual cause/reason. alsamixer and volume control are not muted either, and my sound card is correctly selected as the default.

---

### Post by mahiyar on 2007-01-12
In the same menu of what your png shows there are other options like autodetect etc, can selecting any of the other options make a difference?

---

### Post by ComplexNumber on 2007-01-12
> **mahiyar said:**
> In the same menu of what your png shows there are other options like autodetect etc, can selecting any of the other options make a difference?
tried that. it doesn't make any difference. thats why i selected alsa. it was on autodetect when i first noticed the problem.

---

### Post by ComplexNumber on 2007-01-12
well, i seem to have solved it. or those that are interested in case you have the same problem, the rectification of the problem seems to be in 2 parts:
a) i went into the bios and disabled the default in-built sound card.
b) i turned the volume down on the Realtek AC97 (circled in red in the screenshot of alsamixer).

i originally thought that the ony way to activate the sound was to press the Test button (a detailed above). i assumed that this had the effect of waking up the sound server. however, i was wrong because even when i did that it still didn't turn the sound on. it seemed to be purely random as to when the various sound  applications such as gtick and hydrogen etc would work when i logged in.
HOWEVER, something happened about  half an hour ago. i was messing around with alsamixer when i accidentally clicked on the "Mix Mono" switch. suddenly, a monotonous sound came from the speaker. i couldn't hear any mp3's or any other sound apart from this annoying hum. then i ahd an idea -  i don't know why i didn't realise this before, but i remember that the inbuilt sound card hadn't been disabled in the bios, so i rebooted and disabled it. darn it! i could still hear the monotonous hum ](*,). i opened up alsamixer, and by chance, i switched the AC97 volume right down (as shown in the screenshot). and lo and behold, the hum went and all my missing sounds returned \\:D/  
therefore, my new theory is that the inbuilt sound card was probably creating 'noise' that was 'drowning out' the sound from my default sound card, but because the inbuilt sound card isn't default, that was the reason why i couldn't hear any sound from the various applications. what caused it to be random, i have no idea. i've rebooted several times now, and each time, all my sounds worked perfectly, whereas they didn't before.

---

### Post by mahiyar on 2007-01-12
Sound and Video problems are trickiest to solve, great that u have solved yours, might be useful to other people.

---

### Post by ComplexNumber on 2007-01-12
> **mahiyar said:**
> Sound and Video problems are trickiest to solve, great that u have solved yours, might be useful to other people.
thanks :). i suppose i should have mentioned at the start that i have inserted my own sound card(ie Sound Blaster Live using the emu10k1 driver) and am not using the inbuilt sound card. i think thats a useful tip which i should have heeded earlier on - if you insert your own sound card, disable the inbuilt sound card in the bios.

---

