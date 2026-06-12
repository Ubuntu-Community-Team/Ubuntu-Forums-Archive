---
title: "Sound."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-07
I am unable to listen to any sort of sound on my computer randomly when it worked fine previously. I am unaware of having changed anything to cause this error. How do I fix this, or find what is wrong?

---

### Post by arijarot on 2007-08-07
Checked to see if everything is plugged in/ turned on/ not muted, etc?

---

### Post by CapitanYochua on 2007-08-07
I have. No results.

---

### Post by lakelovers on 2007-08-07
This won't help you but take comfort or discomfort in my sound problem. I lost sound the same way as you: worked then didn't. I have not had sound on my computer for a year or more. I've searched here and followed everything I find. My sound card and speaker check out fine with a test disk from Dell.

---

### Post by arijarot on 2007-08-07
Have a look at this [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by CapitanYochua on 2007-08-07
Not to useful in my case.

---

### Post by CapitanYochua on 2007-08-08
AHH! Using the link given I had little success with the initial steps. So I did the "Get new alsa driver from 
'fresh' kernel" step. I did that and rebooted my computer as directed. When I rebooted my computer no longer starts up with the graphical interface as normal. It basically takes me to a black and white terminal. I am unable to see my desktop or anything of the sort. How do I solve this problem?? I would like to solve this problem even before the sound problem. I even tried booting in recover mode that didn't have any success either. I am having to use a laptop now rather than my desktop.

---

### Post by arijarot on 2007-08-08
I'm sorry to hear that. :confused::( Maybe you can make a new post regarding this new problem or post this on the post from where you took the instructions.

---

### Post by CapitanYochua on 2007-08-09
I was able to resolve that problem. Still have the same sound problems. Any other solutions?

---

### Post by CapitanYochua on 2007-08-09
Okay. so I've been messing around with the terminal and have new info. 
Doing aplay -l I get the error of no sound card found. 
Alsamixer doesn't even run.
Rhythmbox closes as soon as I actually try to play a song.
BUT,
 I can run the command sudo alsamixer successfully. 
I can play *and* hear songs with gksudo rhythmbox.
Doing sudo aplay -l I get back the list of soundcard/s.

 Soo. Now I am starting to suspect that whatever is wrong is just with my user. How can I fix this for user. Any ideas now..?

---

### Post by CapitanYochua on 2007-08-09
sudo module-assistant a-i   alsa-source
doesn't complete without errors either. Seems odd how sudo can recognize sound cards, but not my user. Any explanations for *at least* that?

---

### Post by CapitanYochua on 2007-08-09
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) Following the steps from that given link.
 I get this error...
[http://paste.ubuntu-nl.org/33207/plain/](http://paste.ubuntu-nl.org/33207/plain/)

---

