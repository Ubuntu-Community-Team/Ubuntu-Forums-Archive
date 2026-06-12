---
title: "Microphone in iBook G3"
date: 2005-09-19
forum: Apple PPC Users
---

### Post by RIVE on 2005-09-19
Anyone knows how to make it work? I don't even know if is recognized by the system when i try to use gnome-sound-recorder it's displays this error "Device /dev/dsp does not exist".

My iBook is a G3 500mgz dual USB, the microphone is integrated in the upper right corner of the monitor.

Thanks in advance  :) .

---

### Post by zxee on 2005-09-20
[QUOTE=RIVE]Anyone knows how to make it work? I don't even know if is recognized by the system when i try to use gnome-sound-recorder it's displays this error "Device /dev/dsp does not exist".

My iBook is a G3 500mgz dual USB, the microphone is integrated in the upper right corner of the monitor.

Thanks in advance  :) .[/QUOTE]
 Hi, The error message you provided usually indicates that alsa isn't set up correctly.
I don't have my notes available right now-but I would do a search here for alsa and ppc. Do the system sounds work i.e at start up & when opening applications?

---

### Post by RIVE on 2005-09-20
[QUOTE=zxee]Hi, The error message you provided usually indicates that alsa isn't set up correctly.
I don't have my notes available right now-but I would do a search here for alsa and ppc. Do the system sounds work i.e at start up & when opening applications?[/QUOTE]
 The sound doesn't work in start up, have to check the pcspeakers box in gnome-volume-control first, this only happen in Breezy, but thats not the problem, with warty and hoary the microphone wasn't detected and the sound works just fine, How must be configurated alsa?

Thanks for the help :)

---

### Post by zxee on 2005-09-20
[QUOTE=RIVE]The sound doesn't work in start up, have to check the pcspeakers box in gnome-volume-control first, this only happen in Breezy, but thats not the problem, with warty and hoary the microphone wasn't detected and the sound works just fine, How must be configurated alsa?

Thanks for the help :)[/QUOTE]
 Take a look at this search thread: [http://ubuntuforums.org/showthread.php?t=47476&highlight=alsa+imac+configure](http://ubuntuforums.org/showthread.php?t=47476&highlight=alsa+imac+configure)
I hope that link works..the thread/topic is "mimimal-ppc install specifics" and you want to read the sound section. Hope that helps.

---

### Post by RIVE on 2005-09-22
[QUOTE=zxee]Take a look at this search thread: [http://ubuntuforums.org/showthread.php?t=47476&highlight=alsa+imac+configure](http://ubuntuforums.org/showthread.php?t=47476&highlight=alsa+imac+configure)
I hope that link works..the thread/topic is "mimimal-ppc install specifics" and you want to read the sound section. Hope that helps.[/QUOTE]
 The link you gave me doesn't tell anything about microphone :(, think I will search a little more.  ](*,) 

Thanks anyway :)

---

### Post by Focx on 2005-10-28
Same problem here, had any luck yet? Any suggestions? I'm still on Hoary, using OSS (because with ALSA everything seems to be played too fast...?), same error.

---

