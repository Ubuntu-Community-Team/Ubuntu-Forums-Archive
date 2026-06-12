---
title: "[SOLVED] Can I use my live cd to get my Ubuntu organised again?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by waggygee on 2007-06-15
Recently I have had problems with my Kiba-dock, Beryl and uninstalled programs still showing. Is it possible to use my Live cd to get things back to 'default' without formating my harddrive?

---

### Post by starcraft.man on 2007-06-15
> **waggygee said:**
> Recently I have had problems with my Kiba-dock, Beryl and uninstalled programs still showing. Is it possible to use my Live cd to get things back to 'default' without formating my harddrive?

Uh... no..... what were you expecting the live CD to do? The only way to "get back" to a default is to image your drive with an aptly name "drive imaging suite" when its a clean install (before installing Beryl/Kiba any other unstable/beta apps) and then keep the back up to restore if it fails. I use an imaging suite, [you can find some here]("http://linuxappfinder.com/backupandrecovery/driveimaging"). Partimage is the one most people seem to recommend. So reinstall, then make an image and then you'll always be able to get an operational OS in less than 30 minutes with all your custom tweaks and settings applied.

The live cd doesn't have any magic restore button to my knowledge, damn it why hasn't someone coded the "easy button" from staples? :p

---

### Post by waggygee on 2007-06-15
I was hoping there wounld be a way for my Ubuntu to 'copy' the all the settings and such from the cd (I knew it was a long shot but I had to try). I dont know much about backing up, which of those programs do you suggest. I installed a back up program and set it to automatically do back ups but for some reason it didn't. Oh and if I say weird things that are some what impossible please deal with me, Im new to Linux OS's

---

### Post by starcraft.man on 2007-06-15
> **waggygee said:**
> I was hoping there wounld be a way for my Ubuntu to 'copy' the all the settings and such from the cd (I knew it was a long shot but I had to try). I dont know much about backing up, which of those programs do you suggest. I installed a back up program and set it to automatically do back ups but for some reason it didn't. Oh and if I say weird things that are some what impossible please deal with me, Im new to Linux OS's

I recommend partimage (I use Acronis True Image but thats a paid, proprietary and a bit pro program (has advanced features you don't need). [This tutorial ]("http://www.psychocats.net/ubuntu/partimage")will show you how to make and restore back ups with it for future insurance against problems. Also go to site, they have some documentation.

My suggestion is to do a clean install, customize it with all the apps you know you need and that are official (like from repos, ones you know don't break anything). Then make a clean image. This is your base image, from now until Gutsy keep it as your primary one to go back if you have problems with a later image. Then, put in the less stable programs you use like Beryl, a dock, proprietary blobs like VMware or such and back up entirely again and use this as your incremental and more recent one.

Then you have a perfect backup thats old, and a newer one that is more complete. Then as you go along, make more back ups at your discretion but manage them (delete newer/somewhat older ones as you think is ok, ALWAYS though keep the base image incase of a problem). Thats my system, and it works like a dream.

Oh and you don't say weird things... all questions are welcome :).

---

### Post by waggygee on 2007-06-15
Ok! kool thanks! I'll do that all now

---

### Post by Malta paul on 2007-06-16
I have in fact restored my system with the live disk. It might not be the correct way but it has worked OK for me ;)
a)First I have partitioned my two HD's into four, not including the Ubuntu root and swap ones.
b) then downloaded the added the packages I wanted next backed them up using APTonCD and saved to an ISO file burned on a spare CD.
c) I always keep all my personnel files on the 4 separate partitions. 
Now when I screw up my system - which I rather good at :(  I boot up the live CD and install, till it reaches 'Format Disk'. Then I've manually formatted the /root ONLY. and continued the installation.
The personnel files on the four partitions are still OK [bye the way they were also backed up on to a DVD just in case!]   Then next thing is to use Aptoncd to restore my down loaded packages from the CD. 
Hope this info. is of some help :)

---

### Post by SnakeHips on 2007-06-17
Here's how i got round this today, hope it helps. I'm new at this linux stuff too.

[http://ubuntuforums.org/showthread.php?t=476404&highlight=partimage](http://ubuntuforums.org/showthread.php?t=476404&highlight=partimage)

---

