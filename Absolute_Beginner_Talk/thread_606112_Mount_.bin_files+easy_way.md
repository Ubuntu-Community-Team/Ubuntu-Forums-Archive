---
title: "Mount .bin files+easy way?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by haxer on 2007-11-07
Hi everybody.

Im currently trying everything but nothing wants to get working. 

How to mount an .bin file the easy way?

---

### Post by taurus on 2007-11-07
Is that a binary or movie .bin file are we talking here?

---

### Post by dfreer on 2007-11-07
For a CD image in .bin/.cue format:
[http://ubuntuforums.org/showthread.php?t=93706](http://ubuntuforums.org/showthread.php?t=93706)

---

### Post by carlosjuero on 2007-11-07
have you tried using gMount? I don't know if it supports BIN/CUE but thats what I use for ISO's

---

### Post by haxer on 2007-11-08
> **dfreer said:**
> For a CD image in .bin/.cue format:
[http://ubuntuforums.org/showthread.php?t=93706](http://ubuntuforums.org/showthread.php?t=93706)

Already tried that one without suxxes :P Any more ways? I have the .bin and the .cue file.

And no its not binary files altough the format is .bin its like .iso but the windows version.

---

### Post by haxer on 2007-11-08
*Bump*:guitar:

---

### Post by ruibernardo on 2007-11-08
You can't mount a bin/cue image directly with the mount command. 

If you read the thread that dfreer pointed, you would see that you have to convert the bin/cue file to an iso file with either bchunk or bin2iso. 

Then you can mount it.

EDIT: 

just saw now that you are using Gutsy. Maybe you can use [AcetoneISO2]("http://kde-apps.org/content/show.php?content=44805") - its installation was somewhat complicated in Feisty because of fuseiso, but it should work out of the box in Gutsy (not tested). It isn't in the repositories but there is a package on their website. 

Read the [README]("http://www.acetoneteam.org/gutsy-readme.txt") and download the package from [here]("http://www.acetoneteam.org/download.html") to install.

---

### Post by &#12465;&#12452;&#12488; on 2007-11-08
[http://ubuntuforums.org/showthread.php?t=149963](http://ubuntuforums.org/showthread.php?t=149963)

---

### Post by haxer on 2007-11-08
> **epimeteo said:**
> You can't mount a bin/cue image directly with the mount command. 

If you read the thread that dfreer pointed, you would see that you have to convert the bin/cue file to an iso file with either bchunk or bin2iso. 

Then you can mount it.

EDIT: 

just saw now that you are using Gutsy. Maybe you can use [AcetoneISO2]("http://kde-apps.org/content/show.php?content=44805") - its installation was somewhat complicated in Feisty because of fuseiso, but it should work out of the box in Gutsy (not tested). It isn't in the repositories but there is a package on their website. 

Read the [README]("http://www.acetoneteam.org/gutsy-readme.txt") and download the package from [here]("http://www.acetoneteam.org/download.html") to install.


Thx Acetone2iso works great :) :KS

---

### Post by Cappy on 2007-11-19
Acetone2iso didn't work because I am using 64-bit apparently.

I used bchunk to convert my bin/cue to iso
```
sudo apt-get install bchunk
```
```
bchunk filename.bin filename.iso myconvertedfile
```

---

### Post by bulletxt on 2007-11-20
yes it is clearly stated in the readme that is doesn't support 64-bit and suggest to use iat software giving the link

---

