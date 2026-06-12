---
title: "[SOLVED] sound equalizer for ubuntu gutsy"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-22
hello, 

I've gone through some posts on the subject. I'm wondering if there's any news on the possibility to have a system-wide equalizer for ubuntu. I might be wrong, but I've got the strong feeling that the sound quality (laptop speakers) has somewhat deteriorated since I've switched to Linux. Particularly  when I listen to internet stream radio, but also when I play the usual mp3 files...

thanks for your attention.

---

### Post by Schalken on 2008-03-22
There is no system-wide equaliser that I know of, although it might be possible to create or install one with PulseAudio (which is in Hardy).

WIth regard to the distortion, I recommend turning down both the system-wide volume and the volume of your specific applications to around half-way, because under some situations the system can amplify the audio so much that it gets clipped.

Also try running ```
alsamaixer
``` from a terminal and move the sliders around.

---

### Post by (((X))) on 2008-03-22
Hi

alsamixergui is the graphical frontend for alsamixer

---

### Post by al.adab on 2008-03-22
thanks. Sorry for my ignorance, but how do I run *alsamaixer* on terminal? This is what I got: 

~$ alsamaixer
bash: alsamaixer: command not found

---

### Post by al.adab on 2008-03-22
hold on, I've just realized there was a spelling mistake :)

it's actually *alsamixer*

---

### Post by Schalken on 2008-03-23
Ah, lol, sorry :D

---

