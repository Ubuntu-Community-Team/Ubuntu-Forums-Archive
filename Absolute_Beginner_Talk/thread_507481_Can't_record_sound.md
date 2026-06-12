---
title: "Can't record sound"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by mefl on 2007-07-23
Just loaded on Ububtu 7, got it up and running only to find i can't record sound. i have desktop p/c with an intel MB. any suggestions??

---

### Post by expatCM on 2007-07-23
Enter alsamixer at the command line and check the slider settings for the record options (they are installed as off by default).  To get to the record options you will need to toggle with control and tab ......

---

### Post by ugm6hr on 2007-07-23
If alsamixer doesn't have a setting for Capture - try setting it manually from amixer:
[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

---

### Post by mefl on 2007-07-25
I tryed all the above suggestions peoples but to no availe. i can talk on the mic and listen  to my voice come out of the speakers but when i try to record, it won't. i would set the recorder input to 'mic' then hit record only to see that the input reverst to 'capture'. is that normal???:confused:

---

### Post by ugm6hr on 2007-07-26
I think that the amixer/alsamixer settings need to be changed so that the Input device for "Capture" is the Mic.  That's what I did, anyway (as per previous post linked).  I'm no expert, though, but perhaps worth putting the output from *amixer* here for people to look at.

---

