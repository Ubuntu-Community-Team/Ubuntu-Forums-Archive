---
title: "Graphical Windows and new Video Card"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by gordonsowner on 2007-11-12
Hi,

I have a minor problem.  When I launch graphical applications from a terminal, I get the following:

```

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

```

Not a big deal, as the app starts up.  However, I'd like to make it work smoothly.  I am using a new (to me) video card and had to do new X server config (see: [here]("http://ubuntuforums.org/showthread.php?t=610276")).  I'm wondering if this has anything to do with it, and if there is any quick fixes.

Thanks,

---

### Post by Hospadar on 2007-11-12
it would appear as though this error is related to your sound configuration (and not your video) ALSA is the sound mixer for linux.  I would guess that maybe there is some noise associated with opening windows (or the apps you are using have noises) and that is causing these errors.

Is your sound still working ok?

---

### Post by reacocard on 2007-11-12
it would indeed seem to be sound-related, specifically ALSA is failing to find your sound card. Perhaps the sound card got unseated when the video card was upgraded. Try playing back sound and if that doesn't work, make sure the sound card is firmly seated in its slot.

---

### Post by gordonsowner on 2007-11-13
Ok, this computer *had* a sound card, but I scuttled it for another server -- I just popped it out of it's slot... Can I somehow make it stop looking for the missing soundcard?

thanks,

---

