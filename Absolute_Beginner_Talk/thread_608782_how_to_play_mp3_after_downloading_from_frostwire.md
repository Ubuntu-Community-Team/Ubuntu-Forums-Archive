---
title: "how to play mp3 after downloading from frostwire"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ehtoft on 2007-11-10
Just installed frostwire on ubuntu 7,04. I get the files I want, but can't get any of my sound players to play them, I follow the instructions and install the gstreamers, but still nothing. The soundconverter program wont convert as well. Also, after I install gstreamer, the sound wont work on the original media programs.  Any ideas?

---

### Post by Ashrael on 2007-11-10
Have you installed w32codecs etc?? Take a look here :  [http://www.medibuntu.org/](http://www.medibuntu.org/)
Also isnatlling Xine is usualy a good idea..
And you have to remember that downloading music doesn mean IT IS ACTUALY MUSIC! Nowadays lots of files are corrupted... 

well tell me how you fared?

---

### Post by TadH on 2007-11-10
it does sound like you need xine  or the codecs, i had the same problem.

---

### Post by ehtoft on 2007-11-11
OK! I am ytter novice so I don't know what xine is, but I will look into these suggestions. Thanks a lot! eT Norway

---

### Post by ehtoft on 2007-11-11
OK! I used the add/remove to identify the gstreamer. I also went to the medibuntu site. I'm unsure what I really did, but now can play the mp3 files. Still, some files a mp4. What's that? and why wont they play? I've only ever been a software user (windows) and am illiterate. Can we get the mp4's to work as well? thanks so far....

---

### Post by DutyDuty on 2007-11-11
Do you mean mp4 or m4a? There's a world of difference.

---

### Post by DutyDuty on 2007-11-11
Found this for mp4: ```
sudo apt-get install libmp4v2-0
```

---

### Post by ehtoft on 2007-11-11
thanks for your helps guys/gals. I wish I knew enough to help back. Maybe some day! Windows is soon out of my life!  eT

---

### Post by ehtoft on 2007-11-11
OK, Just took a closer look at the files that wont play. they were mixed; some mp4 and some m4a. What's the difference? eT

---

### Post by DutyDuty on 2007-11-11
mp4 will (probably) play with the install code I gave you. 

m4a, or m4 some other letters are iTunes *only*. I've never heard of non-iTunes programs able to play them.

---

### Post by magicman5421 on 2007-11-11
If you still have itunes, there is an option to convert m4a files to mp3. Or if you have crossover you could just use itunes.

---

### Post by CSMatt on 2007-11-11
M4**p** is the FairPlay restricted file format, but it is highly unlikely that you would ever come across such a file in FrostWire anyway.  M4a is ACC audio and is supported by many other players as well as iTunes.

I recommend installing VLC.  Nice and light and plays almost any format you could want.  But for GStreamer you need to install the "ugly" package, like so:
```
sudo aptitude install gstreamer0.10-plugins-ugly
```
If that doesn't work install the ffmpeg package:
```
sudo aptitude install gstreamer0.10-ffmpeg
```
Both packages require you to enable the "universe" repository.

PS: For your sake I do hope that it is Creative Commons files that you are downloading.

---

### Post by Ashrael on 2007-11-11
i think if you install all the non-free codecs, then you should be able to play m4a files, i just took a look and totem played the file.

---

