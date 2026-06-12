---
title: "Why does 40mb mp3 fill mor than half an 700mb cd?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-05-19
RDNQ: (really dumb newbie question:
 
 How come a 700 mb cd can hold only one 40mb audio file? I have 8 audio files, each almost exactly 40 mb. By my math, that should be about 320mb. How come that won't fit on a single 700mb cd?

---

### Post by Bachstelze on 2007-05-19
Are you sure you burned them as Data CD and not as Audio CD ?

---

### Post by crane on 2007-05-19
What program are you using to write it? There is a good chance it it trying to convert it to an audio cd format.

---

### Post by RH9R on 2007-05-19
Here's where the dumb newb part comes in. in Serpentine - I don't know. In previous burning s/w, it asks if you want data or audio. Will a data cd play in an mp3 player?
 
The other thing I've noticed, is that in Serpentine, I haven't found a way to add or append to a cd that's not full. I just loaded K3B, but haven't used it yet. I'm hoping these options will be much more clear.
 
'Looks like K3B needs a compled lib for mp3 decoding. Other entries say Gnomebaker is good. I'll try that one.
 
Gnomebaker successfully burned all 8 files to a data cd. 'Plays fine on XMMS, not in the car. 'Trying the one disc per file audio cd method for use in the car.
 
Anyone know if Gnomebaker will append files to an unfilled disc?

---

### Post by Jerry N on 2007-05-19
The MP3 players I am familiar with read data disks that contain the MP3 files.  I haven't tried copying MP3 files to a CD using K3B but unless K3B does something strange, it should not need an MP3 add-on.  It would probably need that if it were converting audio disks to MP3 files or creating an audio disk from MP3 files.  You should be creating a data disk, not an audio disk.

Jerry

---

### Post by Bachstelze on 2007-05-19
It needs a plugin if you want to convert the mp3s in Audio CD format. Don't do that, burn as Data CD instead.

---

### Post by RH9R on 2007-05-19
Jerry, and all other kind folks - Thank You!!
 
K3B was taking mp3 files and when I clicked to burn them, 'got a warning msg that I needed Mad mp3 library.
 
Another strange anomoly: I could clearly burn a data cd, holding all 8 files at 320 mb total (each one about 40mb). With Gnomebaker, it burned the data cd just fine. To burn an audio cd (for use in the car), it said one 40mb file is more than will fit on a disc. I go back to soundjuicer, and it made the audio cd just fine. Go figure!
 
So for audio cd formats that play in the car, there's no benefit/advantage to an MP3 format (unless more recent automotive cd players play data discs also.

---

### Post by Bachstelze on 2007-05-19
No. In Audio CD format, it's the duration of the file (80 minutes on a standard CD-R) that is relevant, not their size. But if it reads MP3, the MP3s should be burned on a data CD (they'r enot MP3 anymore if you burn them on an Audio CD ;))

---

### Post by VraiChevalier on 2007-05-19
Audio CD is limited to 70 or 80 minutes regardless of file size. Burning as mp3 files should work in car player. Depending on data rate, I can usually fit about 20 songs in mp3 format on an 80 minute 700Mb CD.

---

### Post by RH9R on 2007-05-19
Thank You All.
 
I appreciate your kind help for the newbie. The kindness is so appreciated. 
 
I didn't know audio is by minutes ONLY. That helps a bunch. 
 
I'd say more, but it would only repeat the gratitude. Thank You!!

---

### Post by Haegin on 2007-05-29
Also remember serpentine is an audio CD only app so it *will* be converting your files to cd audio files. Because of this these CDs will play in the car (assuming you have a normal cd player in your car) whereas data CDs probably wont.
Audio CDs go by minutes because somebody worked out how many minutes of standard CD quality audio fit in 650MB or 700MB (depending on the CD you have). Really it is just the same as size but it makes it easier for people who can't or don't want to understand the wonderful world of bytes (and there is no confusion over how many seconds in a minute unlike the age old 1000 or 1024 issue).

---

### Post by Spike-X on 2007-09-07
> **RH9R said:**
> With Gnomebaker, it burned the data cd just fine. To burn an audio cd (for use in the car), it said one 40mb file is more than will fit on a disc. I go back to soundjuicer, and it made the audio cd just fine. Go figure!
 

I think I know what's happening. For some reason, when you tell GnomeBaker to create an Audio CD, the default setting is for 21 minutes (down the bottom, just next to the Burn button). I don't know why it does this, it's nothing but a pain in the butt, but that's how it is. Your 40Mb MP3 probably goes for longer than 21 minutes, which is why GnomeBaker is telling you it's too big. Just change that setting to 80 min CD, and you'll be good to go.

---

