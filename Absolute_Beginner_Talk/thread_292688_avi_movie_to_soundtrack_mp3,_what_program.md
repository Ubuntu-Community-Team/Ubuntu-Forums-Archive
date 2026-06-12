---
title: "avi movie to soundtrack mp3, what program???"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-11-04
hello
I have been trying to copy the audio from an film(avi), but can not find the program that will do this job. 
I would like to create a film soundtrack from an film stored as avi. 

Need a program,,, please help......



sam

---

### Post by PriceChild on 2006-11-04
Try "audacity" it's available in the repos :)

---

### Post by wannabesurfer on 2006-11-04
tried audacity, but it get stuck when importing audio. I tried also ecawave, mhtwaveedit. any other programs that can do the job?


sam

---

### Post by PriceChild on 2006-11-04
From: [https://help.ubuntu.com/community/AudioApplicationIntroductions](https://help.ubuntu.com/community/AudioApplicationIntroductions)

try Ardour (ardour-gtk)

---

### Post by Lord Illidan on 2006-11-04
EDIT : sry about mencoder, found an easier solution.

 mplayer test.avi -dumpaudio -dumpfile test.mp3

where test.avi is the is the avi you want (so it can be foo.avi) and test.mp3 is the dumped audio file.. (rename it to whatever u want).

---

