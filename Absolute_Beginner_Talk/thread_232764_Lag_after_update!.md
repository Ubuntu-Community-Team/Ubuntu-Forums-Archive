---
title: "Lag after update!"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by junn on 2006-08-09
Ok.. Ive got one major problem:

I installed a fresh version of Ubuntu, plugged in a lan cable and updated using the update manager or whatever its called... I finished updating and rebooted my PC.
When I got to the login screen, that little drum sound startet to lag (playing half the sound over and over again) and my mouse lagged as well. I typed my username but the keyboard wasnt lagging at all which I find very strange... The welcome sound is lagging as well and my mouse keep lagging while in the desktop.

Hope you guys can help me out!

Cheers

---

### Post by bscbrit on 2006-08-09
Is it a USB mouse?  It sounds like a hardware conflict - but I expect someone who knows far more than I do to prove that I am talking rubbish again....

---

### Post by junn on 2006-08-09
it is a USB mouse, yes, but Ive got a lil green adapter so i can plug it in a normal mouse port and its still lagging. So is sound. Im certain that it isnt a hardware malfuncion, because the problems occurred after I updated Ubuntu...

---

### Post by bscbrit on 2006-08-09
Have you tried running update again?

Are there any problems indicated on the very bottom line of Synaptic Package Manager?

Are you using only official repositories? (i.e. could there be a package conflict from another repos?)

---

### Post by kilovh on 2006-12-26
I also have this problem. Did you ever find the solution?

---

### Post by kilovh on 2006-12-26
I wonder if it has anything to do with USB...I have a USB optical mouse and a PS/2 keyboard. I have to boot with noapic acpi=noirq.

---

### Post by K.Mandla on 2007-01-08
Thanks for this. I was suffering with an optical USB mouse piped through a PS/2 port that was lagging as well. I added *noapic acpi=noirq* to my Grub boot line and all is fine now. Cheers! :D

---

### Post by sureinlux on 2007-02-06
Hi there,
 This may be a little tangential, but just to fix the random hang-ups and reboots I passed ```
noapic acpi=noirq
``` during boot. Although it has not hung so far (~8hrs), there is no audio output at all.
 Any thoughts on this will be really great. Also exactly what does the ```
noapic acpi=noirq
``` boot option do???

---

### Post by sureinlux on 2007-02-06
this is the error message

Hi there,
 This may be a little tangential, but just to fix the random hang-ups and reboots I passed ```
noapic acpi=noirq
``` during boot. Although it has not hung so far (~8hrs), there is no audio output at all.

```
ALSA lib pcm_direct.c:819:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to initialize slave
ALSA snd_pcm_open error: Invalid argument
libao - OSS cannot set channels to 2
ALSA lib pcm_direct.c:819:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to initialize slave
Creating link /home/me/.kde/socket-mylappy.
can't create mcop directory
```

 Any thoughts on this will be really great. Also exactly what does the noapic acpi=noirq boot option do???

---

