---
title: "[SOLVED] powerISO for linux? create an iso for a dvd?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-29
if I have a directory called VIDEO_TS, how do I make an ISO out of all those files and burn them to a dvd?

sv

---

### Post by mattman on 2007-12-29
I use K3B. You don't even need to make an iso first. In the New Project menu choose New Video DVD PRoject and then dran your files into the VIDEO_TS and AUDIO_TS folders.

---

### Post by dasunst3r on 2007-12-29
I remember trying to burn the VIDEO_TS folder as a data project, but it didn't work on regular set-top players.

---

### Post by mattman on 2007-12-29
> **dasunst3r said:**
> I remember trying to burn the VIDEO_TS folder as a data project, but it didn't work on regular set-top players.
If you don't choose to make a New Video DVD Project it won''t format the disk properly.

---

### Post by staticvoid on 2007-12-29
cool thanx.

so brasero can't do it huh..?

i'll tell ya'll how it goes.

and nice blog mattman


sv

---

### Post by mattman on 2007-12-29
IMHO K3B is the best most feature rich burning app for linux. If you didn't have it installed before now make sure you install libk3b2-extracodecs or libk3b2-mp3 so that you can convert mp3 to audio cd format if you ever have the need to do that.

---

### Post by Paulmd on 2007-12-29
> **staticvoid said:**
> if I have a directory called VIDEO_TS, how do I make an ISO out of all those files and burn them to a dvd?

sv


Is this a commercial disk, that you are attempting to back up? Or is it a home video type thing?

If it's commercial, there are 2 major technical hurdles. (Legal hurdles aside)

1) Most commercial dvds have too much data to fit on a standard dvd-r. Your movie disks hold 9 gb of data to a standard dvd-r's 4.7

2) CSS: content scrambling. DVDs are protected by encryption. The encryption is weak, but the movie industry has aggressively went after websites who host programs to break it.

There are windows-based freeware programs that overcome both hurdles, But their legality is questionable in many locales. (we can discuss which freeware programs work, privately, as long as you promise me that you're not copying rental DVDs, or otherwise pirating)


If this is a home-brew video project, k3b should do the trick.

---

### Post by staticvoid on 2007-12-29
ok, thanks for the info, Paulmd.

it's an extracted ISO image from a non commercial disk, so it should be ok.

if k3b can't do it i'll just get the trial version of poweriso onto our junky windoze pc and do it there. :)

or shall i pm you about linux software to do the task? I always use the roxio burn kit that came with our pc to copy DVD's that friends have made, it would be good for me to learn to do it in linux. and i'm not piriting :) promise.

thanks for all the help! (and yes, i agree with you mattman, k3b is definitly more feature rich :)

sv

---

### Post by Paulmd on 2007-12-29
> **staticvoid said:**
> ok, thanks for the info, Paulmd.

it's an extracted ISO image from a non commercial disk, so it should be ok.

if k3b can't do it i'll just get the trial version of poweriso onto our junky windoze pc and do it there. :)

or shall i pm you about linux software to do the task? I always use the roxio burn kit that came with our pc to copy DVD's that friends have made, it would be good for me to learn to do it in linux. and i'm not piriting :) promise.

thanks for all the help! (and yes, i agree with you mattman, k3b is definitly more feature rich :)

sv

K3b should work as long as the video is not content-protected, and fits on a standard dvd-r

I'm not all that familiar with linux software that defeats css.  All I have is a source code for a c program, that takes the VOB files and descrambles them.

Is it the ISO image itself, or files pulled from an ISO?

If it's just an ISO file, it's simple enough to burn that with k3b. 


The structure of a typical dvd:

Contains 2 directories:

AUDIO_TS
VIDEO_TS

AUDIO_TS is usually empty. The meat is in VIDEO_TS.

VIDEO_TS contains a file named VIDEO_TS.VOB, also VIDEO_TS.IFO, and VIDEO_TS.BUP.

a vob file is the meat. the video itself.

[http://en.wikipedia.org/wiki/VOB](http://en.wikipedia.org/wiki/VOB)

IFO files
[http://en.wikipedia.org/wiki/IFO](http://en.wikipedia.org/wiki/IFO)

BUP files
[http://en.wikipedia.org/wiki/BUP](http://en.wikipedia.org/wiki/BUP)

---

### Post by staticvoid on 2007-12-29
cool, yeah... there is no AUDIO_TS folder, should I make one? even if its empty?

yeah the ISO is just a buncha VOB, IFO BUP files etc. and thanx for the wikis. good to know :)

sv

---

### Post by Paulmd on 2007-12-29
> **staticvoid said:**
> cool, yeah... there is no AUDIO_TS folder, should I make one? even if its empty?

yeah the ISO is just a buncha VOB, IFO BUP files etc. and thanx for the wikis. good to know :)

sv

probably no need to have an AUDIO_TS, no harm either, tho'.

---

