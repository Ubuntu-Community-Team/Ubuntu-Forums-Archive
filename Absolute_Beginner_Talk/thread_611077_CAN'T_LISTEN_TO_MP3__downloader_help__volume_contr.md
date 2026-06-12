---
title: "CAN'T LISTEN TO MP3 / downloader help / volume control....!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Attila2452 on 2007-11-12
what do i do? i tried to use music players but i cant seem to find a MP3 playing one. 

i also want a music downloader (ubuntu)

& my volume wont work like if i go to youtube or something, i cant hear it enough, my spkrs would be at like MAX & my comp would be MAX (keyboard shrt cut) but all that comes out is a stuped little muffle of a distorted sound! i have even tried going to vol. control  & turning up my volume ro changed my provider thing but nothing works i really need help!

---

### Post by Adrenal on 2007-11-12
Music Player - None, except vlc, will play mp3 out of the box. You need to install the codecs. Open an mp3 in movie player(open the program, drag the mp3 in) and you will be prompted to install the codecs.

Music downloader - I assume you mean something like limewire. It has a linux version.

No idea, except maybe check that your speakers are plugged in

---

### Post by peedeeramone on 2007-11-12
for mp3s and other "restricted" media or whatever you just need to download the codecs. I thought ubuntu would ask to download them for you but maybe not...  either way try 

sudo apt-get install ubuntu-restricted  or something of that matter

or you could just install automatix and have it do it for you.



for music downloader i assume you mean a p2p client such as limewire.  i would go with frostwire. its cross platform and basically the same as limewire pro, but free and blue. its open source if that means anything to you.


as for your volume, i really dont know whats the deal with that.


good luck

---

### Post by Pumalite on 2007-11-12
Sudo apt-get install ubuntu-restricted-extras
Also add Medibuntu to your sources list and download all the codecs:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by Attila2452 on 2007-11-12
I FIXED IT!!!   

i had to go to:
Vol. control
Edit
Prefrences
scroll down until you see "Line-in"

[COLOR="Red"]**MAKE SURE THAT BOX _IS_ CHECKED!!!!!**[/COLOR]

there you have it :)

---

### Post by Pumalite on 2007-11-12
If you want a lamp to work, plug it in the outlet first.

---

