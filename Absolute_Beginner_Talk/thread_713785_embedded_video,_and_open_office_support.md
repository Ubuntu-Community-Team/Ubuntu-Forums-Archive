---
title: "embedded video, and open office support"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by crackatoe on 2008-03-03
Hello all. 

I am  trying to run a power point slide show in Open office, and it has two embedded video files. These files won't play, and according to the 'properties' function, are identified with Intel Video codec 5.   Is there a way to convert these to something OO can play (embedded), or is there linux support for codec 5 somewhere out there in the community?  FYI, the two video files end in  an ".avi" and are in the same folder with the slide show.  Thank you.

---

### Post by tdrusk on 2008-03-03
```
sudo apt-get install ubuntu-restricted
```
That should get you the right codecs. If that doesn't work you can convert it with Mencoder.

---

### Post by crackatoe on 2008-03-04
Thank you.  I got this error message. 

: Couldn't find package ubuntu-restricted


What other kind of embedded video file can play within Open Office?

---

