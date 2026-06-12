---
title: "Reinstalling Ubuntu due to performance problems - help"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by mrapoc on 2007-12-17
Basically, I couldnt enable any effects without the performance going to pot previously. I also had random artifacts bottom right of screen and sometimes on the cursor. I want to reinstall and this time ensure i get the graphics driver installed correctly. Could some1 post a step by step to install the latest ATI driver (for a x1900gt), plus any other programs i'll need for general use (video plugins for films, mp3, etc.)

THanks :guitar:

---

### Post by kpkeerthi on 2007-12-17
[ATi Binary Driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882")

[Multimedia]("https://help.ubuntu.com/community/UserDocumentation#head-5ba01a2a950ca4281bc039ebd2ab3da97af09732")

---

### Post by siciliancasanova on 2007-12-17
media, install the gstreamer codecs

---

### Post by CatKiller on 2007-12-17
You don't really need to reinstall the whole operating system to get one package reconfigured, you know.

---

### Post by mrapoc on 2007-12-17
hmmm perhaps 

just seems like ive installed ubuntu + vista lol

feel ive messed around with it too much to have a good system

As for before i had

Amarok
Azeurus (ewww but its the only one my tracker allows atm) 
DeVeDe
Dvdrip
AIGLX
Compiz 


hmm

---

### Post by CatKiller on 2007-12-18
> **mrapoc said:**
> feel ive messed around with it too much to have a good system

You can change anything that you want on your Ubuntu computer. Which means you can change it all back if you want to. Not being able to change things back so that your computer fills with crap that you don't want, doing things that you don't want, so the whole thing becomes a pain, is a Windows thing. Honestly.

If there's anything that you want to get back into the state when it was first installed, you can run ```
sudo dpkg-reconfigure <package name>
``` A common example of this would be ```
sudo dpkg-reconfigure xserver-xorg
``` to re-run the graphics configuration scripts. This is useful, for example, if you've been fiddling with your X configuration and didn't make a back-up of your xorg.conf file, and you've made it so that you can't start the GUI. This can be used to fix it from the command line.

You also don't need to periodically re-install the operating system because your files are fragmented and refuse to go back together, since the Linux filesystems don't fragment files. The registry doesn't get full of entries that don't go away when you uninstall the programs that made them, making lookups painfully slow, because there is no central registry.

Your Linux experience will not degrade over time, and anything that you've broken or mis-configured can be fixed. Occasionally, for a new user, a re-install can be easier than learning enough about their system to fix it, but it isn't, in general, strictly necessary.

---

### Post by mrapoc on 2007-12-18
Referring back to my poor performance issue - especially while browsing, seems to be fixed by turning "composite" off. Why is this? It also means i cant have any nice visual effects on. Surely this isnt right?

---

### Post by froghunter on 2007-12-18
Have you tried the most recent ATI driver? I am not sure if this is the one Ubuntu automatically goes after, but I got myself into a load of trouble trying to disable and then re-load a later driver, but I haven't seen if this works with my ATI X300 card. [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) . Good luck.

---

### Post by mrapoc on 2007-12-18
It is the latest driver that ive installed..but again whenever composite is on (allowing any effects at all) everything goes sluggish and browsing goes jittery, like described in that ATI binary link :confused::confused:

---

### Post by shae on 2007-12-18
That is one of the bugs in the current ATI driver.  It will hopefully be fixed in the near future.  For now AGLIX+Compiz is basically unusable.  And by the way the distortions are a leftover from the watermarking issue and is fixed by adding the following to your device section of your xorg.conf file:

```
Option          "XAANoOffscreenPixmaps" "true"
```

---

### Post by mrapoc on 2007-12-18
So basically...until ATI releases the next one...i cant have any effects
Unless I run the alternative to AGLIX which was the massive resource hog one...still sucked

---

### Post by froghunter on 2007-12-18
Well, I tried the new driver, and when I ran aticonfig, it gave me quite a few options. Now, I am a complete noob, but the first step was configuring the driver, and I never got this to work, but I really think it could be done. Once you get aitconfig, the first step is
 ```
aticonfig --initial --input=/etc/X11/xorg.conf
```
 but when I run this
```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
```
Right now if I type```
 aticonfig --initial=check
```, I get ```
Check: No fglrx section
```. So I don't think I have the wrong driver taken over yet, but am using the generic still, which is slow, but it works. Any help on this? Maybe a solution is around?

---

### Post by froghunter on 2007-12-21
So, I am total noob, but I think for Envy to work, you have to go ahead and at least load the other driver. This is what I did (in way too much detail.
[http://ubuntuforums.org/showthread.php?p=3975191#post3975191](http://ubuntuforums.org/showthread.php?p=3975191#post3975191)

---

