---
title: "firefox flash faint sound"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by marine63 on 2008-03-30
X( help i looked at many other threads of the same issue but non of them helped me :(

---

### Post by Michael.Godawski on 2008-03-30
what exactly is your problem? did the sound worked some time? did you try to reinstall the flash plugin?

---

### Post by marine63 on 2008-03-30
when i'm playing a song on youtube i can only hear it faintly. I'm not really sure what i'm doing. I've been following tutorials that I found on google but non of them worked for me. 
This is the song i am testing on so far i can only hear the lyrics (faintly) [http://www.youtube.com/watch?v=H8RgMU9YYvA](http://www.youtube.com/watch?v=H8RgMU9YYvA) which starts @ 1:17. Yes, I did try reinstalling adobe flash plugin but it didnt do anything.
so far, this is the only thing thats keeping me from transferring over to ubuntu from winxp :(

---

### Post by Michael.Godawski on 2008-03-30
and this is the only problem with the sound? when you play songs files on your machine the sound volume is fine?

try to reinstall the flash plugin:
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by marine63 on 2008-03-30
crud -_- i just tried playing a mp3 on my computer and it didnt work :( i hear it faintly too

---

### Post by Michael.Godawski on 2008-03-30
run in terminal 
 ```
alsamixer
``` 

and increase the volume of master and pcm

---

### Post by marine63 on 2008-03-30
:( both were already at 100 percent

---

### Post by Michael.Godawski on 2008-03-30
when you go to system > preferences > sound and do a sound test to sound playback is everything fine?

---

### Post by marine63 on 2008-03-30
YAY I GOT IT TO WORK TY!!!
the pcm and master was on high and everything else was on low.
all i had to do was make everything to max :o TY SIR!!!
silly me >.>

---

### Post by LowSky on 2008-03-30
this might sound stupid but have you made sure you have your speaker plug in the correct input and that its all the way in, also if the speakers or headphone have there own volume adjust that as well.

---

### Post by marine63 on 2008-03-30
my problem been fixed already so... nothing to see here shoo >.>

---

