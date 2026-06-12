---
title: "Amarok"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-09-29
Im trying to get Amarok to play MP3 files (yes i know Linux doesnt like MP3) ive got the codec for it to work on Rythombox, but is there one for Amarok, or is it just MP3 dead?

---

### Post by Iarwain ben-adar on 2006-09-29
Hi,
normally on the newest Amarok (in the repo's) you can try to play an mp3,
and if you don't have the right codecs, Amarok asks you if it can install those..


Iarwain

---

### Post by Drakkor on 2006-09-29
Ubuntu loves mp3s, I think you have to either hard wire,eeh\go from scratch to enable mp3 support or go through easyubuntu or automatix to enable all the codecs support. I use amarok all the time, plays excellently,lol :p

---

### Post by Captain Kirk76 on 2006-09-29
Rythombox is playing fine, with the MP3 codec i got, when i play in Amarok, it just says MP3 files are currently not supported :(

---

### Post by Iarwain ben-adar on 2006-09-29
Is your Amarok up-to-date?
Mine is 1.4.3


Iarwain

---

### Post by Captain Kirk76 on 2006-09-29
This is the exact quote

Amarok 1.4.3 (Using KDE 3.5.2) 

Funny, i thought Ubuntu used GNOME?

---

### Post by Mimsy on 2006-09-29
There is a package called libxine-extracodecs (I think I got that name right), that you need to download to make Amarok play mp3. That solved my problem, that was pretty much the same as yours. My version of Amarok, 1.4.3, can now play mp3 files.

/Mimsy

---

### Post by Captain Kirk76 on 2006-09-29
Could you give me the correct code to type into Terminal to get that package?

---

### Post by Iarwain ben-adar on 2006-09-29
Here you go :D
```
sudo apt-get install libxine-extracodecs
```


Iarwain

---

### Post by Mimsy on 2006-09-29
Okay, I went back and looked at the week-old thread where I had the same problem, and libxine-extracodecs is the name of the package. I installed it through Synaptic, and it works just fine.

Edit:
Or you can use the code Iarwin suggested, and do it via the terminal. :)

/Mimsy

---

### Post by Captain Kirk76 on 2006-09-29
Thanks a heap you guys, very helpfull!

---

### Post by Mimsy on 2006-09-29
So it worked then? :)

/Mimsy

---

