---
title: "Noise when playing music"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by E-Jey on 2006-05-31
I using ubuntu for a week. To play my music, i've installed the packages from this wiki: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) There is only one problem, there is some noise when I play music. I don't have it when i play exactly the same song on the same machine with windows. To find out what the problem is, I installed several media players. It doens't help. I tried to play some flac files, there is still noise. I gues there is a problem with the sound card drivers. I use the on board soundcard from my nforce 4 chipset. 

How could I update my soundcard drivers? It's really annoying. Thanks in advance!

---

### Post by PriceChild on 2006-05-31
Is the sound only there when playing files? or there while ubuntu is logged in also?

---

### Post by E-Jey on 2006-05-31
[QUOTE=PriceChild]Is the sound only there when playing files? or there while ubuntu is logged in also?[/QUOTE]

What do you mean? There is only noizy when i play music.

---

### Post by Lord Illidan on 2006-05-31
Your PCM and WAVE volumes are too high.

Type alsamixer into a terminal, and change the volumes. Use the arrow keys left and right to change specific volume, and use the up and down key to change the volume itself.

Master can be left at 100%

Do it while music is playing so you can adjust it to your ears perfectly.

Press esc to exit, then type sudo alsactl store

---

### Post by E-Jey on 2006-05-31
[QUOTE=Lord Illidan]Your PCM and WAVE volumes are too high.

Type alsamixer into a terminal, and change the volumes. Use the arrow keys left and right to change specific volume, and use the up and down key to change the volume itself.

Master can be left at 100%

Do it while music is playing so you can adjust it to your ears perfectly.

Press esc to exit, then type sudo alsactl store[/QUOTE]

It works :D Thanks!

---

### Post by Pugaciov on 2006-05-31
[QUOTE=E-Jey]It works :D Thanks![/QUOTE]

I had the same problem when I played mp3s on Ubuntu for the first time :-D

---

