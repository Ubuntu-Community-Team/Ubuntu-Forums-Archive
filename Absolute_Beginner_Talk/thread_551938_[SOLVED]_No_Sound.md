---
title: "[SOLVED] No Sound"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by candive on 2007-09-15
I Have no sound when I play a music CD or on u tube, I'm using Ubuntu Feisty Fawn 7.04 :confused:
I have sound when I run in windows.

All Ubuntu updates are current.
I believe I have found all volume controls.

Any suggestions would be appreciated.

Thank you.

---

### Post by st33med on 2007-09-15
What is your sound card to find out:
```
lspci
```

And post it here.

---

### Post by Dr Small on 2007-09-15
Check your BIOS settings, and make sure the audio is [Enabled] and not [Auto]

Dr Small

---

### Post by Canic on 2007-09-15
I am a long time windows user but a n00b linux user
I know this subject has been explained to death, but I have searched every forum I can think of and nothing is working... I'm |--| this close to wiping my hard drive and going back to m$. My specs are as follows;
Linux Ubuntu 7.04
nVidia ck804 mobo
nVidia gForce 7300 gs graphics
Sound Blaster Audigy 24-bit HD (purchased today in hopes of solving the problem... it didn't)

Heres the deal... I installed ubuntu and the sound worked perfectly, every which way I used it is was there for me. However my graphics card was not functioning properly... so I installed the proper drivers for the graphics card and voila! 3d acceleration achieved. So here I am enjoying my shiny graphics when I notice something wrong... no sound (using onboard soundcard)... I've spent the last 3 days searching forums and trying everything, I've even purchased a new soundcard in hopes of an easy fix... but alas my computer remains soundless... plz help me

---

### Post by st33med on 2007-09-15
Also, I had the same prob as you one time and discovered that it was my volume manager! To go to the GUI, System>>Preferences>>Volume Manager.

Or something like that.

---

### Post by Canic on 2007-09-15
nothing... everything is set to the new soundcard (which linux recognizes)... and nothing

---

### Post by splintercellguy on 2007-09-15
> **Canic said:**
> I am a long time windows user but a n00b linux user
I know this subject has been explained to death, but I have searched every forum I can think of and nothing is working... I'm |--| this close to wiping my hard drive and going back to m$. My specs are as follows;
Linux Ubuntu 7.04
nVidia ck804 mobo
nVidia gForce 7300 gs graphics
Sound Blaster Audigy 24-bit HD (purchased today in hopes of solving the problem... it didn't)

Heres the deal... I installed ubuntu and the sound worked perfectly, every which way I used it is was there for me. However my graphics card was not functioning properly... so I installed the proper drivers for the graphics card and voila! 3d acceleration achieved. So here I am enjoying my shiny graphics when I notice something wrong... no sound (using onboard soundcard)... I've spent the last 3 days searching forums and trying everything, I've even purchased a new soundcard in hopes of an easy fix... but alas my computer remains soundless... plz help me

Disable the CK804 in BIOS, and check your analog/digital setting in mixer.

---

### Post by Canic on 2007-09-15
thank you.... you guys did in half an hour what i couldn't do in 3 days... the community is by far the best aspect of linux... thank you very much

---

### Post by st33med on 2007-09-15
Your welcome.
Mark this post as solved, please!

---

### Post by nonewmsgs on 2007-09-15
diabling the ck804.  is that a particular soundchip in the mb or is that just the onboard sound card?

---

### Post by Canic on 2007-09-16
> **st33med said:**
> Your welcome.
Mark this post as solved, please!

Pardon the n00b question but... solved? is that something the thread starter does or am I missing the link for it?

---

### Post by candive on 2008-06-10
Problem solved with 7.10
Thank you

---

