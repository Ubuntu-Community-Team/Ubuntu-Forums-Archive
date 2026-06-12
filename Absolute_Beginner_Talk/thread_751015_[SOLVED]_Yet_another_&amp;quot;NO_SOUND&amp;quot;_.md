---
title: "[SOLVED] Yet another &amp;quot;NO SOUND&amp;quot; problem"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-10
Hello all
 I was attempting to install Gutsy on a HP dv6000 (C2Duo T5500, 2GB DDR2 RAM, nVidia 8400 GT, 160GB HDD, Realtek sound card). Ofcourse everything else was perfect but the sound. I tried all sound options (ALSA, OSS etc) but no use. What would be the solution?

---

### Post by erginemr on 2008-04-10
Hello,

What is your exact problem? No sound, choppy sound?..

---

### Post by sayakb on 2008-04-10
> **erginemr said:**
> Hello,
 
What is your exact problem? No sound, choppy sound?..
 
No sound at all.

---

### Post by erginemr on 2008-04-10
Well, to get more info on your sound chip please post the output of the following commands from the terminal:
```
aplay -l
```
```
lspci | grep -i audio
```
```
cat /proc/asound/cards
```
and the (error) message from:
```
alsamixer
```

---

### Post by sayakb on 2008-04-12
> **erginemr said:**
> Well, to get more info on your sound chip please post the output of the following commands from the terminal:
```
aplay -l
``````
lspci | grep -i audio
``````
cat /proc/asound/cards
```and the (error) message from:
```
alsamixer
```

Sorry for the terrible delay. I would post the outputs as soon as he brings his laptop to me .

---

### Post by sayakb on 2008-04-17
Thank you. I seem to have resolved it myself!! I installed "Linux-backports-modules" and the sound started working.

---

### Post by erginemr on 2008-04-17
No problem. ;)

For further insight to the issue and for future reference:
[http://ubuntuforums.org/showpost.php?p=4582215&postcount=42](http://ubuntuforums.org/showpost.php?p=4582215&postcount=42)
[http://ubuntuforums.org/showpost.php?p=4574654&postcount=10](http://ubuntuforums.org/showpost.php?p=4574654&postcount=10)

---

### Post by sayakb on 2008-04-17
> **erginemr said:**
> No problem. ;)
 
For further insight to the issue and for future reference:
[http://ubuntuforums.org/showpost.php?p=4582215&postcount=42](http://ubuntuforums.org/showpost.php?p=4582215&postcount=42)
[http://ubuntuforums.org/showpost.php?p=4574654&postcount=10](http://ubuntuforums.org/showpost.php?p=4574654&postcount=10)
 
Yepp.. looks like your first link worked for me :D

---

