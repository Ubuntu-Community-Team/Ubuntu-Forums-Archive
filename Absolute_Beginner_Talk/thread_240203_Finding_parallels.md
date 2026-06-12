---
title: "Finding parallels"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by chromaglow on 2006-08-20
So i am trying to install paralles...

i have downloaded it, unpacked it and add programs says it is installed but it is nowhere to be found please help.

i even downloaded debian to try and find it but after following the steps i can't find that either

help!

---

### Post by David Corrales on 2006-08-20
For me, it's under System Tools. Open a terminal and type "parallels" and see if it works.

---

### Post by chromaglow on 2006-08-20
Dave, 
this is the terminal screen i get

/usr/lib/parallels/parallels-linux: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

any advice

---

### Post by David Corrales on 2006-08-20
Hey chroma, I just replied to your other post. Actually you're really close to getting it running.
Run **sudo apt-get install libtq3-mt** and the next time it'll boot up :)

---

