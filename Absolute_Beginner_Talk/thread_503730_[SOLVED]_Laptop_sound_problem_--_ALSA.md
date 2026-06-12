---
title: "[SOLVED] Laptop sound problem -- ALSA"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by st0nes on 2007-07-18
Hi all.  I bought a new laptop (proline style note) a few days ago, running Ubuntu 7.04.  I have struggled since then to get the sound working; trying all solutions from this forum and others, to limited avail.  The problem in the beginning was that I had no sound at all on my headphones and very low volume from the built-in speaker.  My sound card is on-board Intel HDA VIA VT82xx.

I found a partial solution to the original problem: adding the line 
```
options snd-hda-intel model=ref
```
to the /etc/modprobe.d/alsa-base file.

Now the speaker is working correctly, but I am getting very low volume from the headphones with all sliders in alsamixer up at 100%.  An interesting thing is that the speaker volume is controlled by the headphones slider and the headphone volume is controlled by the front slider.  It looks as though alsa has got this all **** about tit.

Any solutions?

---

### Post by expatCM on 2007-07-18
I have found sound problems to be a total distraction in Ubuntu ...  it is a joy when it works and works properly but when it does not ... you are somewhat alone since others share your problem who also do not know the solution.

Perhaps this link could help you out a bit
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by st0nes on 2007-07-19
A quick update: this isn't specifically an Ubuntu problem, it is a problem with the snd-hda-intel driver.  If I could just find a way to route the headphone output in the alsamixer to the headphones instead of the speaker, all would be well (I will never use the speaker in any case).  I'm fairly sure this is not an insurmountable problem -- I just need to find someone with the necessary expertise to tell me how to do it.  To that end, I have logged a bug (#3246) with ALSA and am awaiting their response.

---

### Post by st0nes on 2007-07-20
OK, no joy.  Perhaps if I restate the question differently (this is a two part question, so pay attention and stop picking your nose): 1. ALSA is a dog's breakfast; is there any other audio library out there that may do a better job?  2. If not, is there a file I can edit to redirect the output of a channel to a different device?  If I can't get this working I'm going to have to dump Ubuntu which would be very sad because in all other respects I'm very happy with it.

---

### Post by expatCM on 2007-07-20
You say
> ALSA is a dog's breakfast;
I think that is very very true.  Not just ALSA but the whole matter of sound, it is really painful to find your way round and you never ever know if there is something else to discover.

You ask
> is there a file I can edit to redirect the output of a channel to a different device
Have you looked at asoundconf?   If you enter "asoundconf list" at the command line you can see the available devices, asoundconf will show you the syntax of changing the default.

If what you are wishing to do is to capture / playback the sound then have a look round Audacity, there may well be the settings you need, indeed the information from Audacity may help you otherwise in seeing what is available with your laptop.

---

### Post by st0nes on 2007-07-23
Thanks expatCM, asoundconf list just gives the name of the only card I have.  I'll download audacity this evening and see if it has any settings ideas.

---

### Post by st0nes on 2007-08-01
The only solution to this turned out to be upgrading my kernel to a later one that recognised my hardware.  Very clear instructions on how to do this can be found [here]("http://ubuntuforums.org/showthread.php?t=511974&highlight=upgrade+kernel").

Thanks to all who tried to assist

---

