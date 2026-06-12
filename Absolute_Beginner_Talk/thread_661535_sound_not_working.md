---
title: "sound not working"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by winsall on 2008-01-08
jeez the forum must hate me by now, i have so many questions :P

my next problem is, my sound isnt working.

a quick check with aplay -l reveals:

winnie@winnie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

which means it knows my sound card is there (i think).

but still i get no sound :(
anyone know the answer? help is always greatly appreciated

thanks in advance,
winsall

---

### Post by peabody on 2008-01-08
What's alsamixer say?  Are any of your output sources muted perchance?

---

### Post by winsall on 2008-01-08
sorry im still kinda new how to i find out what alsa mixer says?

---

### Post by peabody on 2008-01-08
Just type alsamixer at a terminal.

You can also use the volume control applet in the bottom right hand corner next to the clock if running Gnome.

---

### Post by winsall on 2008-01-08
hmm alsamixer is showing all is on and (doesnt appear) to be muted

---

### Post by peabody on 2008-01-08
I know this is a very windows-ish remedy, but does the problem persist between reboots?

---

### Post by winsall on 2008-01-08
heh heh

yeah i just rebooted then, nothin.

interesting note, the volume control lists 2 devices:

HDA INTEL (ALSA MIXER) which was shown when i did aplay -l

but also REALTEK ALC883 (OSS mixer)

i switched to the realtek, which was muted, however this didnt fix it.

DANG thought i was so close!!!

---

### Post by peabody on 2008-01-08
You want the alsa version.  Have you tried turning looking at all of the volume levels to see if any of them have been turned all the way down?

---

### Post by Raptor45 on 2008-01-08
This may or may not be relevant.

For my laptop, ubuntu incorrectly picks the wrong output. Try going to System>Preferences>Sound and at the bottom make sure HDA Intel (ALSA) and PCM are selected.

For me, I also had to correct which thing the audio applet controlled.

---

### Post by winsall on 2008-01-08
hmm all great suggestions but unfortunately it just isnt working

ubuntu doesnt want to make it easy for me XD

but im not gonna give up!

---

### Post by anaconda on 2008-01-08
do you belong to "audio" group.. ie. do you have the permissions to use your audio?

type (in terminal):
```
groups
```
it will show you what groups you belong currently.

I had this problem with my machine..

---

### Post by winsall on 2008-01-08
winnie@winnie-laptop:~$ groups
winnie adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin


nope, dang.

i dont quite understand, after all it was working in 7.4 (i remember watching half the ubuntu humanity to others video clip)
im sure its fixable tho! im not giving up on ubuntu just yet

---

### Post by uBeer on 2008-01-08
There are some good places on the forum to look for if you're having sound troubles.
There is good guide here: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
Maybe installing the latest alsa drivers will fix it, worked for me thankfully.
Good luck!

---

