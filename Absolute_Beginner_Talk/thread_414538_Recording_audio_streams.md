---
title: "Recording audio streams???"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by nayo on 2007-04-19
Hi.  I need to record audio streams from company web sites for transcription purposes.  Is there some program to translate a stream into an honest audio file that I can put on my hard drive?   Thanks!!!!!!!!!

---

### Post by josesanders on 2007-04-20
Audacity should do that.  I believe it's in the repos, so to install, all you have to do is run:

$ sudo apt-get install audacity

When you run the program, change the input to "vol" or something like that, and when you record, you should get the audio stream from the internet.  At least it worked for me.

---

### Post by theonlykman on 2007-06-03
ok, I dont get this. When I used xp, audacity was the bomb..but now its confusing as hell and I cant record anything. Heres a screen of the input choices that I have...and none of them work for anything. I would like to be able to record streams...check out my the screen of my audacity preferences...

---

### Post by theonlykman on 2007-06-03
screenshot below

---

### Post by Kilz on 2007-06-03
You could also use kstreamripper

---

### Post by jiminycricket on 2007-06-03
The Audacity in Ubuntu is old and uses deprecated software like GTK1, OSS, etc.  You might try installing the updated Debian package here, but there are no guarantees it will work (look for i386 on that page): [http://packages.debian.org/unstable/sound/audacity](http://packages.debian.org/unstable/sound/audacity).  Gutsy Gibbon will have the next version of it BTW.

A [guide]("http://liquidat.wordpress.com/2007/05/07/howto-record-soundcard-output-with-audacity-in-kde/") to record.

---

### Post by theonlykman on 2007-06-05
Only like, what, 4 more months until Gutsy's released? It feels like I was downloading the Feisty beta yesterday...time really flies...

---

