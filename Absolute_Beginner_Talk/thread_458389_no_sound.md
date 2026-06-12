---
title: "no sound"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Simran on 2007-05-29
Hi,

I've made a fresh install of ubuntu 7.04 on my laptop and i've got no sound, so i'm guessing i need to set it up or install some drivers ??

I don't know where to start .. :confused:

Any assistance would be greatly appreciated.

Simran

---

### Post by mkoehler on 2007-05-29
Can you give us the make and model of the sound card / integrated sound hardware you are using?

---

### Post by Simran on 2007-05-29
> Can you give us the make and model of the sound card / integrated sound hardware you are using?

*noob alert* i would if i knew where to find that information. :(

Simran

---

### Post by quinnten83 on 2007-05-29
try with command lspci and check the output regarding the soundcard.
Otherwise copy the entire output in this thread and someone will be able to help you.

---

### Post by Simran on 2007-05-29
> try with command lspci and check the output regarding the soundcard.
Otherwise copy the entire output in this thread and someone will be able to help you.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by reckless2k2 on 2007-05-29
[http://linux-on-laptops.com/forum/archive/index.php/t-1488.html](http://linux-on-laptops.com/forum/archive/index.php/t-1488.html)

That is going to give you a little info. Someone will be able to go further if you need it.

---

### Post by Simran on 2007-05-29
Thanks, i'll check it out :)

---

### Post by Sparkster185 on 2007-05-29
I have the exact same sound card in my latop (Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)), I finally got it working this past weekend.  Try this:

Add "options snd-hda-intel model=3stack" at the end of /etc/modprobe.d/alsa-base. Restart.  Let me know if this works for you.

---

### Post by Simran on 2007-05-29
> I have the exact same sound card in my latop (Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)), I finally got it working this past weekend. Try this:

Add "options snd-hda-intel model=3stack" at the end of /etc/modprobe.d/alsa-base. Restart. Let me know if this works for you.

done, done and DONE! yeah it worked :) thanks very much.
*you can go in the hero list in my sig :P*

Simran

---

