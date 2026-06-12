---
title: "[SOLVED] Normalising audio volume in gtkpod"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2008-01-01
Hello Everybody,

How do you get the 'normalize volume' function in GTKPOD to work? Every time I use it it says that it cannot normalize. Looking at the preferences section of GTKPOD, under normalize, it asks for a path, presumably to something that'll make the function work. Can anybody tell me what to put in this box?

Thanks, as always,

Charlie

---

### Post by blueridgedog on 2008-01-01
normalize-audio

Install with:

sudo apt-get install normalize-audio

Then located:

/usr/bin/normalize-audio

---

### Post by Charlie Chick on 2008-01-01
Hi blueridgedog,

Thanks for your suggestion. Unfortunately, it doesn't work. I get an error message saying that the audio "could not be normalised". Do you have any further suggestions, please?

Thanks.

---

### Post by Charlie Chick on 2008-01-01
Update:

blueridgedog's suggestion got me thinking. I typed 'mp3' into Synaptic and found 'mp3gain' which appeared to do what I wanted it to do. I downloaded and installed it and it works!

Thanks to blueridgedog for pointing me in the right direction.

Charlie

---

