---
title: "Making Major Volume Adjustments"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by SamsLembas on 2007-05-06
I have just gotten Ubuntu set up on an old computer, and everything is working perfectly, but the sound is far too soft, even when the normal volume control is all the way up. How can I make major changes to the volume?


Thanks in advanced.

---

### Post by overdrank on 2007-05-06
> **SamsLembas said:**
> I have just gotten Ubuntu set up on an old computer, and everything is working perfectly, but the sound is far too soft, even when the normal volume control is all the way up. How can I make major changes to the volume?


Thanks in advanced.

Hi if you are using edgy, you can double click on the volume control if gives you more options. Good luck!

---

### Post by SamsLembas on 2007-05-06
I am using Feisty Fawn. It brings up a menu here too, but it does not allow major volume adjustments to be made.

---

### Post by zvacet on 2007-05-06
When sound control window show go to the edit and choose what are you want to see in window.Then you can make adjustment with it.

---

### Post by chalex on 2007-05-06
You can try the command "alsamixer" from the command line.

---

### Post by SamsLembas on 2007-05-06
None of that helps. I already have all of those cranked up as high as possible, yet the sound is barely audible.

---

### Post by cam2009 on 2007-05-06
I had the same problem. Do you have a Toshiba Satellite laptop? I fixed it by entering something in the terminal, but I went through many things that didn't work first, and I can't seem to find it again.

EDIT:

found it. in terminal:

> sudo gedit  /etc/modprobe.d/alsa-base

scroll down to the bottom and add this:
> 
options snd-hda-intel model=auto

you'll have to completely restart for it to work. though this may not work if it's a different computer than mine, as I've heard different versions of this problem.

---

### Post by SamsLembas on 2007-05-07
I am using an HP Pavilion 753, with Polk Audio speakers. I think they came with the machine, but I cannot be sure. They are just whatever I pulled out of my basement a few days ago. ;)

I gave that tip a try anyway, but to no avail. It seemed to be messing a lot of stuff up right away (my screen was flickering on and off) so I reverted to my backup before even trying to play any sounds.

---

