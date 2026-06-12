---
title: "I've lost audio input"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-03-22
Hi from a beginer
Somehow I have lost audio input, i can't use skype.
I have an alsa driver, i have unistall and reinstalled the driver using synaptic but still no good results.
Any help
thanks
koli

---

### Post by schwascore on 2007-03-24
One of the most common problems is the mic input being turned off or at 0% volume.

Run alsamixer:
```
josh@sexybeast:~$ alsamixer
```

and then use the arrow keys to select the mic input and turn it all the way up.  Hopefully the fix is that  simple.  Good luck.

---

### Post by sn0m on 2007-03-25
no mate thats not the case, mic levels, input levels are at maximum.

---

### Post by sn0m on 2007-03-25
Is this too difficult to get any sort of answers. does any of the experts know how to completely remove the sound and re-install it again, or shall I wait for the next feisty release?

---

