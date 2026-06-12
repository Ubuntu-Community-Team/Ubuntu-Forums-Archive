---
title: "Can't install XMMS, aMSN, Mplyer"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by x-ph on 2006-01-05
When I choose 'Add Applications' and select from the list XMMS player or MPlayer there comes a message 'The application can not be found in your archive. This usually means that it is not available for your hardware plattform.' When I choose aMSN it says: 'Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'amsn'.'. I tryed but I couldn't do anything in the 'Advanced mode' (maybe bacause it is for advanced users :P, not for beginners like me). I know it is not of my hardware plattform because I've ran them when I was using the Ubuntu 5.10 live CD. Can someone help? Thanks in advance!

---

### Post by briguy on 2006-01-05
Try adding them using Synaptic (under System -> Administration) instead of "Add Applications".

---

### Post by x-ph on 2006-01-05
Yeah, this is the so called 'Advanced' mode :) When I try to add aMSN it says that it depends on uninstallable packages. And XMMS and MPlayer doesn't exist there. It's stupid because I can run them using Live CD and cannot using the installed ubuntu...

---

### Post by Lord Illidan on 2006-01-05
Use the Ubuntu Guide : [Ubuntu Wiki (community-edited website)]("http://www.ubuntulinux.org/wiki/FrontPage")

---

### Post by patrick295767 on 2006-01-05
For me, I do: 

with my sources.list of breezy
[http://ubuntuforums.org/showthread.php?t=70942&highlight=sources.list](http://ubuntuforums.org/showthread.php?t=70942&highlight=sources.list)
  
 
```
apt-get -f install xmms
apt-get -f install amsn
```

then, from amsn, website, the autopackage works to install amsn above it
(still one tiny prob. that I dont knwo with my server installation)

I hope that I helped a bit bit

Greetz

---

