---
title: "mp3 encoder"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-12-19
Does anyone know of a good mp3 editor / encoder?  I have Audacity, but am also looking for something that I can trim the file size with as well as the length (ex. 192 kbps -> 128 kbps).

Thanks.

---

### Post by paulmilliken on 2005-12-19
[QUOTE=amcavoy]Does anyone know of a good mp3 editor / encoder?  I have Audacity, but am also looking for something that I can trim the file size with as well as the length (ex. 192 kbps -> 128 kbps).

Thanks.[/QUOTE]
You can trim the length of the raw wave file before compressing it with a program called sox.  One of the options is trim.  Type "man sox" for details.  lame is a good mp3 encoder.  Type "man lame" for details (assuming you have it installed).

Paul

---

### Post by kosmic on 2005-12-19
You can do that in audacity :) just open the file go to preferences and set to save with a Mp3 bitrate of 96 (for example) then export as mp3 :) and voila

---

### Post by daschl on 2005-12-19
if you want something really nice with an graphical interface take a look at Grip (you can download it with synaptic)

if you want to try another real nice program, try "abcde" (a better cd encoder ;))

(also available in the apt-get repository)

use LAME for encoding your tracks :)

---

### Post by amcavoy on 2005-12-21
Thanks for the suggestions :smile:.  I found what I need in Audacity (as has been suggested).  I just needed to change the bitrate.  I'll have to check out Grip though; it looks like a good program.

Thanks again!

---

