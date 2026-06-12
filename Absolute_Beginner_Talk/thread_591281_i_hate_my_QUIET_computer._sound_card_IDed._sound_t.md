---
title: "i hate my QUIET computer. sound card IDed. sound to low."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by sdinh07 on 2007-10-25
i have a toshiba a105-s4004 with realtek alc861 sound card. my sound card is recognised by the system and i have tried turning up the volume on every control possible. even the alsamixer one in terminal. all i get is faint sound that can only be heard if i put my ear up close to the speaker. using headphones i get louder sound with a lot of static. it's still not as loud as when i was running windows. please help. i want my music back.

---

### Post by sdinh07 on 2007-10-25
sorry about the horrendous spelling. i'm just so frustrated.

---

### Post by FuturePilot on 2007-10-25
Please post the output of 
```
lspci | grep audio
```

---

### Post by sdinh07 on 2007-10-25
that didn't yield anything.
when i put in lspci | grep -i audio it spit this out. i just saw that command online somewhere after googling the first one online.
```
scott@scott-laptop:~$ lspci | grep -i  audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

---

### Post by FuturePilot on 2007-10-25
Looks like there is a problem with that card
[https://bugs.launchpad.net/malone/+bug/85869]("https://bugs.launchpad.net/malone/+bug/85869")
However it looks like some people have had success with this 
```
gksudo gedit /etc/modprobe.d/alsabase
```
And add this line to it.
```
options snd-hda-intel position_fix=1 model=3stack
```
Save and reboot.

---

### Post by sdinh07 on 2007-10-25
you like freaking rock. that did the trick. i can now hear these babies playing from my bedroom while i'm in the next room taking a leak.

---

### Post by logoodnix on 2007-10-27
It worked for me as well,  but only sort of...when i put the volume past a certain level  (about half way) the sound becomes distorted and uncontrolled, so much so it seems like it may damage my speakers. 
Any suggestions on how to approach this?

---

### Post by FuturePilot on 2007-10-27
Make sure you're not controlling PCM. Go to System>Preferences>Sound and towards the bottom there should be a list of Mixer Tracks. Make sure PCM isn't highlighted. You probably want Master.

---

### Post by logoodnix on 2007-10-27
Thanx, I took the GNOME volume control off of the taskbar at it's highest performance point. Also I used GNOME ALSA mixer to tweak a bit.
Workin' perfect now!!!:)

---

