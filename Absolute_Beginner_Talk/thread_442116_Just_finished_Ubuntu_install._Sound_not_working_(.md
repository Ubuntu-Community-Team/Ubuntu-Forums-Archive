---
title: "Just finished Ubuntu install. Sound not working :("
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by neogarfield on 2007-05-13
Hi all,
After all the reading up, I finally installed Ubuntu today. But my sound isnt working :(
I installed Ubuntu 7.04 64x for my Intel 64x PC. My sound card is HDA-Intel.

I read through numerous threads, and numerous web pages, but I still cant get my sound to work. I tried doing everything each page seemed to say, without understanding half of what they said. Seemes to me like I reinstalled my sound drivers (ALSA?) 5 or 6 times!!!

What should I do? What information do you need to help me out. Please tell me what to type and do to get the info.

Thanks a lot,
Mohan

---

### Post by gilgongo on 2007-05-13
I had this problem once. It might not be the same as yours though, but this is what I did to solve it:

Open a command line, type "alsamixer" (without the inverted commas) - shield your eyes from the resulting excuse for a user interface - and see if PCM is at anything less than 100, or if "Front" or "Surround" have an "MM" (mute) at the bottom. If the volume of PCM is low, raise it with the up arrow on the keyboard, if stuff is showing "MM" press the "m" key on the keyboard to unmute it.

---

### Post by neogarfield on 2007-05-13
Hmmm... I had already done that, but I hadnt noticed the "surrond" at MM. Fixed the surround to 100 as well, but its still a no go... No sound.. :(

---

### Post by annda on 2007-05-13
see if the card is used by the system - can you post the output of this command?

```
cat /proc/asound/cards
```

---

### Post by neogarfield on 2007-05-13
Annda, thanks for the help. Here's the output.

```

neogarfield@NGinTux:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xff43c000 irq 16


```

---

### Post by annda on 2007-05-13
this looks good. have you unmuted everything in alsamixer?

do you use headphones? the intel-hda driver is not perfect. on my laptop, i get sound from both speakers&headphones if they are plugged in. after i unplug them, no sound at all. ckeck that too.

---

### Post by neogarfield on 2007-05-13
Yeah I've unmuted everything. No, I dont use headphones. Yes, speakers are plugged in, I tried replugging them too.

No go... No sound yet :(

---

### Post by annda on 2007-05-13
sorry, Mohan, i have no more ideas at the moment. try playing around with system>preferences>sound and booting with your speakers plugged in and not. i know, it doesn't sound very competent. i am not.

---

