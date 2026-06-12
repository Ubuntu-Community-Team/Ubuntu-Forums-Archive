---
title: "[SOLVED] Activated Service"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Officer Dibble on 2007-10-04
I have activated the highlighted service in this attached image and now I don't have any sound. Nothing changes after I deactivate this service or restart the computer.

How do I get my sound back please? :(

---

### Post by maryjanua on 2007-10-04
try uninstalling then reinstalling alsa

---

### Post by Officer Dibble on 2007-10-04
> **maryjanua said:**
> try uninstalling then reinstalling alsa

Nope, didn't work... :(

It's a service that was originally disabled, but because I experimented with enabling it my sound isn't working now.

Will this mean a reinstall of Ubuntu? :confused:

---

### Post by Officer Dibble on 2007-10-04
Please help... I need access to audio books. :(

---

### Post by Malibu Illusion on 2007-10-04
```
sudo aptitude install alsa-utils
```

Then:

```
alsamixer
```

Make sure all of those bars are up to their maximum.  You should then receive audio.  If not:

```
aplay -l
```

And post output.

Take care.

---

### Post by Officer Dibble on 2007-10-04
Not all the bars were at maximum so here are the results of the final instruction you gave me:

> **** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thank you very much for your help here.

Maybe I should add that it was working fine from the point of install and over many weeks, and only flopped when I enabled the ALSA doo-daar in the Services menu.

Thanks again.

---

### Post by nowshining on 2007-10-05
open up preferences - sound and select in the drop down menu another selection and each one click the test button, do u hear any beeps when u do so, one may or not give an error - in advance info. on that.

---

### Post by Officer Dibble on 2007-10-05
> **nowshining said:**
> open up preferences - sound and select in the drop down menu another selection and each one click the test button, do u hear any beeps when u do so, one may or not give an error - in advance info. on that.

Not a peep from it... and thats after trying the different combinations too. There wasn't any errors reported at all - just no sound. :(

I am dual booting with XP and there is no problem with the sound there. It is definitely down to something I have done with Ubuntu when I selected that ALSA option.

---

### Post by Farhan on 2007-10-05
if you think you have correctly installed ALSA*, check if you have all the audio channels unmuted (try installing gnome-alsamixer, that is pretty handy a tool if you don't want to use the console based alsa mixer).

* see if you have correctly installed alsa-base, alsa-utils and alsa-tools

---

### Post by Officer Dibble on 2007-10-05
> **Farhan said:**
> if you think you have correctly installed ALSA*, check if you have all the audio channels unmuted (try installing gnome-alsamixer, that is pretty handy a tool if you don't want to use the console based alsa mixer).

* see if you have correctly installed alsa-base, alsa-utils and alsa-tools

You guys never cease to amaze me!! This fixed the problem!!! :guitar:

I knew it couldn't be a problem with Ubuntu and that it was something I was missing or doing wrong.

Thank you so very very very much all of you for having a share in sorting out this problem and to Farhan for finding a lid to it as a result of the friendly team effort. :)

---

### Post by nowshining on 2007-10-25
> **Officer Dibble said:**
> You guys never cease to amaze me!! This fixed the problem!!! :guitar:

I knew it couldn't be a problem with Ubuntu and that it was something I was missing or doing wrong.

Thank you so very very very much all of you for having a share in sorting out this problem and to Farhan for finding a lid to it as a result of the friendly team effort. :)
u know I accidently disabled it and had this exact same problem. :) u know if u didn't ever ask how to fix it on the forums here and such I would of been trying everywhere to find a solution altho oddly the alsamixer from the terminal didn't help..oh well pcm was disabled..lolz :P

---

