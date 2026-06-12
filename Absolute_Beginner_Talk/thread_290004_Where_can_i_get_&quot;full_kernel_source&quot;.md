---
title: "Where can i get &quot;full kernel source&quot;?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Xphome on 2006-10-31
When i try to install my ALSA drivers it say that it cant find the "full kernel source" in /usr/src/linux. Where can i download the "full kernel source" or where in / is it?

---

### Post by Xphome on 2006-10-31
i think this was the wrong forum, cant delete the topic.

---

### Post by plb on 2006-10-31
How are you trying to install alsa? Never had to do it on Ubuntu but on debian it's just apt-get install alsa-base alsa-utils then run alsaconf and once finished "alsactl store"

---

### Post by jpkotta on 2006-10-31
Run ```
uname -a
``` and look for the version of the kernel.  Mine is 2.6.15.  Don't worry about all the sub-sub-...-sub version numbers.  Then ```
sudo apt-get install linux-source-2.6.15
```  If ```
ls /usr/src/linux/
``` returns nothing, then you have to extract and link the source tree.  The trailing '/' is significant here.```
cd /usr/src
sudo tar jxvf linux-source-2.6.15.tar.bz2
sudo ln -s linux-source-2.6.15
```

---

### Post by David Corrales on 2006-10-31
The last command jpkotta listed, I think, should be:
**sudo ln -s /usr/src/linux-source-2.6.15 linux**
so a link called *linux* actually gets created.

---

### Post by devilsadvocate1987 on 2006-10-31
I believe you dont have to install ALSA in ubuntu... in any case, you can get the linux headers from the repositories. Also, try a apt-cache search alsa to see what they have there.

---

