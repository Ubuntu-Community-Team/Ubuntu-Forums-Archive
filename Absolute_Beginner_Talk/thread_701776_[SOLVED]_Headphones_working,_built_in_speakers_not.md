---
title: "[SOLVED] Headphones working, built in speakers not."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by TheWhatkin on 2008-02-19
I installed Ubuntu 7.10 earlier this week as a dual boot, and for some reason the built in speakers on my laptop don't work, but headphones do.

Help?

---

### Post by northern lights on 2008-02-19
Can you post the output of ```
cat /proc/asound/cards
``` and maybe ```
cat /etc/asound.conf
```? Are your headphones USB or analog plug?

---

### Post by benfindlay on 2008-02-19
Might seem stupid, but lets just rule something out first:

Try double clicking on the volume icon next to the clock and choosing Edit>Preferences. Tick both Master and Master Mono if they arent ticked then try turning up both volumes. And un-mute any that are muted also!

Hope this helps!

---

### Post by TheWhatkin on 2008-02-19
*fiddles with settings* There's no Master or Master Mono option, but checking 'surround' gets speaker output. Initial problem solved!

However:
a) Now the speakers don't shut off when the headphones are plugged in.
b) The 'PC Speaker' slider(which is the one controlled by the vol up/vol down/mute buttons on my keyboard) no longer works.

In case it's still relevant:

genevieve@genevieve-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0440000 irq 22
genevieve@genevieve-laptop:~$ cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

The headphones are analogue.

---

### Post by northern lights on 2008-02-19
It wasn't relevant in the sense that I thought - namely your headphones being USB and you thus having two sound devices - still I revealed your sound card's nature - Intel HDA - and that's the core of the problem.

There's an excellent HowTo that should solve your problem [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

---

### Post by benfindlay on 2008-02-20
> **TheWhatkin said:**
> *fiddles with settings* There's no Master or Master Mono option, but checking 'surround' gets speaker output. Initial problem solved!

However:
a) Now the speakers don't shut off when the headphones are plugged in.
b) The 'PC Speaker' slider(which is the one controlled by the vol up/vol down/mute buttons on my keyboard) no longer works.

In case it's still relevant:

genevieve@genevieve-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0440000 irq 22
genevieve@genevieve-laptop:~$ cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

The headphones are analogue.

Right click on the volume icon next to the clock and choose preferences, you can pick which volume to control with the icon there!

Hope this helps!

---

### Post by TheWhatkin on 2008-02-20
The HowTo worked, thanks!

---

