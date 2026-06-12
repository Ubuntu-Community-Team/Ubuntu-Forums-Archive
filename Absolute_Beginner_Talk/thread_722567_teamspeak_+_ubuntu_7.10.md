---
title: "teamspeak + ubuntu 7.10"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by erpa on 2008-03-12
Hi there, i recently switched from windows to ubuntu, with little effort and some reading trough this forum i've been able to make evrything work till now, so thx for u excellent work :D. My problem actually is that i can't make teamspeak work properly. I know TS use oss so  i run it when no other programs are using the audio, the problem is that it doesn't allways work just like now: i switched on my pc and the first program i ran was TS, i connected to server and i saw ppl speaking (the green light turned on) but i couldn't hear or speak and i was not muted (like when u have others programs using the audio channel). I tried using alsa/oss mixer too, but somthing is wrong too, in fact when i run "aoss teamspeak" from my terminal i got muted.
I hope someone can help me, thx again and sorry for my bad english

---

### Post by kjm61287 on 2008-03-12
aoss should work, make sure you have alsa-oss installed through the Synaptic Package Manager.Also, here's a tidbit I learned on the way, I had a similar issue to yours. 

Go to System\Preferences\Main Menu (assuming you are running Gnome, idk what it will be for KDE). In Main Menu, if you go to System\Preferences at the bottom, Multimedia Systems Selector probably isn't checked and if it isn't, check it. 

After making Multimedia Systems Selector visible, you should be able to go to that and select OSS/ALSA (or PulseAudio if you adventurous) and what device you want to use. I know using aoss teamspeak and having ALSA for input/output in MSS worked fine for me.

I hope that helps!

---

### Post by erpa on 2008-03-12
hi again, i've done like u suggested, but nothing new. First i selected ALSA as plugin and then i choose the right devices but when logged in Ts i couldn't here or speak even if not muted. Then i tried to install again alsa-oss pack and run aoss teamspeak, but  i was muted like if something else was using the audio channel. The thing making me mad is that somtimes it works and somtimes it doesn't so it's even harder to figure out what's wrong. I thought it could be a problem with dirvers but using other programs like skype i have no problems. I'm still looking for help, thx :D

---

### Post by ODF on 2008-03-12
Is everything is okay in your alsamixer

Just type 'alsamixer' into a terminal.

Sometimes XMMS cause some issues because it use as OSS as default. Do you have XMMS installed ?

---

### Post by erpa on 2008-03-13
i don't have XMMS installed and here is what i get when i run alsa mixer

---

### Post by erpa on 2008-03-14
noone else can help me? thx in advice

---

### Post by erpa on 2008-03-21
Sorry for bothering again, i'm still searching a way to fix the problem, lately TS isn't working any more and i noticed that it's not only a problem with TS but with any application using OSS (i have the sam problem using programs trough wine). If someone can help me it would be very appreciated! :D

---

