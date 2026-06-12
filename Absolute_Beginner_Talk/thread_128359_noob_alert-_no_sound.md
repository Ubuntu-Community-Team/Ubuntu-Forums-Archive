---
title: "noob alert- no sound"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by el_ricardo on 2006-02-11
there is no output on my soundcard, the ALSA drivers are installed, and i've updated them but nothing seems to work, going on preferences > multimedia selection and testing gives no results, but it doesn't tell me that its not working, it just plays the test file as if there was an output. i'm using winamp, and running it through wine, should is there an output plugin i should download for linux (even though that would make little difference at this stage because it doesn't seem to be working anyway)

cheers :)

---

### Post by cogadh on 2006-02-11
This is going to sound silly, but have you checked your volume controls? By default, Linux has the master volume turned all the way down on the system. For my own system, I found that I had to raise the master as well as individual channel (right, left, center analog) volume before I got sound.

---

### Post by el_ricardo on 2006-02-11
lol thats got it, can't believe i overlooked that, it was also trying to send sound to a soundcard that doesn't even exist, in a hard drive that isn't even connected, but the sound is working, i just had to switch the output device to realtec whatever and then turn the different channels up

---

