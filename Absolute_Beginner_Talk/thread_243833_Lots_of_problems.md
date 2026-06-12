---
title: "Lots of problems"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by CBondra on 2006-08-25
Hi guys. I just installed Ubuntu Linux today, I was up all night last night reading about it. Deprived of sleep, I didn't think of backing up my drivers before installing it and swiping the Windows I had on it. Now i'm stuck installing NDisWrapper, I get the most ridiculous errors. Can somebody give me a step by step on how to install the driver for my wireless card (Broadcom 4306 PCI)?

I would GREATLY GREATLY appreciate that, and any other tips that you have :)

---

### Post by CBondra on 2006-08-25
:X anybody?

---

### Post by derred on 2006-08-25
I don't know if this is what you're looking for but it worked for me

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")

I'm sorry if it's not what you had in mind but... it was the first thing i could think of. If it doesn't help, post youre hardware details so we can get a better feeling for your problem.;)

---

### Post by dca on 2006-08-25
Is this similar?
 
[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

---

### Post by sailor2001 on 2006-08-25
google sourceforge and look for "lists"   find your driver there and download it..untar and copy to desktop. It will have an "inf" extention. then in terminal:
cd Desktop    (notice D is in caps)   
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i NET8180.INF (yours will be different)
sudo ndiswrapper -l
sudo dhclient
ctrl/x

I think there is another way listed in the forums that maybe better

---

### Post by CBondra on 2006-08-26
Thank you guys so much! I got it working

---

